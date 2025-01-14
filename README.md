<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>

</p>
<p>

<b> Deploying an on-premises Active Directory (AD) environment within Azure Virtual Machines (VMs) allows organizations to extend their identity and access management infrastructure to the cloud. This setup provides centralized authentication for both on-premises and cloud resources. Below is a step-by-step guide to implementing AD Domain Services (AD DS) on Azure VMs: </b>

<h2> Plan Your Network Architecture </h2>

Virtual Network (VNet): Create a VNet in Azure to host your AD DS environment. Ensure the IP address range does not overlap with your on-premises network if a hybrid setup is planned.

Subnets: Divide the VNet into subnets. It's recommended to have a dedicated subnet for AD DS to enhance security and manageability.

Network Security Groups (NSGs): Configure NSGs to control inbound and outbound traffic to your subnets. Allow necessary ports for AD DS, such as LDAP (port 389), Kerberos (port 88), and DNS (port 53).
</p>
<br />

<p>

</p>
<p>

<h2> Deploy Azure Virtual Machines </h2>

<b>Create VMs </b> : Deploy at least two Windows Server VMs to act as domain controllers, ensuring high availability. Place them in an Availability Set or across Availability Zones to protect against hardware failures.

<b> VM Sizing </b> : Choose VM sizes based on the expected authentication load. Monitor performance and adjust as needed. 
TERMINALWORKS

Static IP Addresses: Assign static private IP addresses to the VMs to ensure consistent network identity. This can be configured through the Azure portal or PowerShell.
</p>
<br />

<p>
<h2> Configure DNS Settings </h2>

DNS Configuration: Set the Azure VNet to use the IP addresses of your domain controllers as DNS servers. This ensures that any VMs added to the VNet can locate and join the domain.

<h2> Install Active Directory Domain Services </h2>

Remote Desktop Access: Use Remote Desktop to connect to each VM.

Install AD DS Role: On each VM, use the Server Manager to install the Active Directory Domain Services role.

Promote to Domain Controller: After installation, promote the server to a domain controller. For the first VM, create a new forest. For subsequent VMs, add them as additional domain controllers in the existing domain.

<h2> Configure Active Directory Sites and Services </h2>

<b> Site Configuration </b> : Define Active Directory sites to represent the Azure environment. This helps optimize authentication and replication traffic.

<b> Replication </b> : Ensure replication between domain controllers is functioning correctly. Adjust replication schedules and site links as necessary.

</p>
<p>

Secure the Domain Controllers

Updates and Patching: Regularly apply security updates to the domain controllers.

Access Controls: Limit administrative access to the VMs. Implement Just-In-Time (JIT) access and multi-factor authentication (MFA) for added security.

Backup and Recovery: Implement a backup strategy for the domain controllers to ensure you can recover from failures or data loss.

<h2> Join Other Azure VMs to the Domain </h2>

VM Configuration: Configure other Azure VMs to use the domain controllers as their DNS servers.

Domain Join: Use the System Properties on each VM to join them to the domain.

<h2> Monitor and Maintain the Environment </h2>

Monitoring: Use Azure Monitor and other tools to keep track of the health and performance of your domain controllers.

Maintenance: Regularly review and maintain the AD DS environment, including user accounts, group policies, and security settings.

</p>
<br />
