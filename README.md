# Welcome to Microsoft SDN GitHub Repo
This repo includes scripts, templates, and sample switch configurations to aid admins in deploying the Windows Server 2016 Software Defined Networking (SDN) Stack and connecting it to their existing network topologies. It also includes sample diagnostics and examples for attaching Windows Container endpoints to a virtual network in additon to other tenant workflows. 

The first step in any SDN Deployment involves planning and working with a network administrator to ensure the correct IP subnets and VLANs are used as well as switch port configuration settings (e.g. VLANs to trunk, possibly DCB settings) which connect the Hyper-V Hosts (physical servers) to the physical network.   To plan and deploy Microsoft SDN, refer to the following topics on Microsoft TechNet:
* [Plan a Software Defined Network Infrastructure](https://technet.microsoft.com/en-us/library/mt605207.aspx)
* [Deploy a Software Defined Network Infrastructure](https://technet.microsoft.com/en-us/library/mt590901.aspx)

## SDN Fabric Components and Deployment Options  
The Windows Server 2016 (WS2016) SDN Stack consists of several new services and roles, not least of which is the Network Controller. The first step in the deployment is choosing the method by which you will install and configure the Network Controller. This can be done in a number of ways:
 * System Center Virtual Machine Manager (SCVMM) 'VMMExpress' PowerShell scripts 
 * **(recommended)** 'SDNExpress' PowerShell scripts with DSC configuration
 * SCVMM Console (GUI) Configuration and Service Template Deployment

### Network Controller 
The Network Controller role exposes a RESTful API through which management systems (e.g. SCVMM, PowerShell, etc.) can create network resources and policy using a published API and JSON schema. This API can be invoked through Network Controller PowerShell modules or the SCVMM Console. 
> Note: The Windows Server 2016 SDN Platform has more capabilities than those exposed through System Center Virtual Machine Manager (SCVMM)

It can also be called directly using the Invoke-WebRequest PowerShell module (or curl) and appropriate HTTP GET, POST, DELETE methods with JSON Body and/or Returned output.   

After the Network Controller is deployed, additional SDN fabric services and infrastructure VM(s) - Software Load Balancer Multiplexers, RRAS (SDN) Gateways - can be created and attached to the Network Controller. After each service and infrastructure VM is deployed, new tenant scenarios will become available.  
> Note: It is important to note that simple tenant operations such as creating an Overlay Virtual Network and attaching VMs to can be done immediately after the Network Controller is installed without any other services (e.g. SLB or Gateway) deployed. 

Tenant Scenarios available after Network Controller deployed:
 1. Create Overlay Virtual Network 
 2. Create virtual subnets
 3. Create VM NICs to attach VMs to a virtual subnet 
 4. Create Network Security Groups Access Control Lists (ACLs) and apply these to virtual subnets or VM NICs
 5. Create QoS policy for setting bandwitch caps or inbound port reservations and apply these to VM NICs

### SDNExpress 
The SDNExpress scripts will 


At a minimum, a user will need to download the SDNExpress scripts to a host from which deployment will occur. The directory containing the SDNExpress scripts will need to have Read/Write permissions open for all hosts to be used in the deployment. The FabricConfig.psd1 configuration file will need to be customized for your environment and will be used by the SDNExpress.ps1 script to setup the SDN fabric resources. After the fabric resources are setup, the SDNExpressTenant.ps1 script can be run to create a sample, single-tenant, two-tier application (Web and Database) which uses default ACLs and two virtual subnets. 



=======
The SDNExpress folder contains six folders: 

* **AgentConf**

  The AgentConf folder holds fresh copies of OVSDB schemas used by the SDN Host Agent on each Windows Server 2016 Hyper-V host to program network policy.

* **TenantApps**

 The TenantApps folder contains sample configuration for a two-tier application (Web and Database) deployment.
 
* **Tools**

 The Tools folder is a place you can put any files that you want to automatically copied to your hosts and virtual machines.

* **Certs**

 This is a temporary location for certificates created during deployment.

* **Images**

 This is where you copy your operating system VHDX  files.


* **Scripts**

  The scripts folder contains PowerShell and Desired State Configuration (DSC) scripts used to configure both fabric and tenant resources in a sample SDN deployment.




Click **Clone or download** on the Microsoft SDN repository to download the SDN-master.zip file. Read and follow the planning and deployment topics referenced below to deploy Microsoft SDN in your datacenter.

To plan and deploy Microsoft SDN, refer to the following topics on Microsoft TechNet:
* [Plan a Software Defined Network Infrastructure](https://technet.microsoft.com/en-us/library/mt605207.aspx)
* [Deploy a Software Defined Network Infrastructure](https://technet.microsoft.com/en-us/library/mt590901.aspx)


This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.