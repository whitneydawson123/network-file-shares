<p>
<img src="https://github.com/whitneydawson123/network-file-shares/assets/94804621/9ade7ad0-a20c-4592-91e1-2960e1b59b71" alt="network logo"/>
</p>

<h1>Network Files Shares and Permissions</h1>
In this project, we will create file shares with different permissions and attempt to access them<br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machine, Domain Controller, Client Machine)
- Remote Desktop
- Active Directory Domain Services
- Shared Network Files

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)
- Windows Server 2022

<h2>File Shares and Observations</h2>

<p>
Log into DC-1 as your domain admins account. In my case, it's mydomain.com\jane_admin. 
<br/>
  
Log into Client-1 as a normal user.
</p>

<p>
<img src="https://github.com/whitneydawson123/network-file-shares/assets/94804621/5505ef6c-082d-4f9c-934b-3fabbda20459" height="80%" width="80%" alt="Step 1"/>
</p>
<p>
Go back to DC-1, go to the C:\ drive, and create four folders "read-access", "write-access", "no-access", and "accounting".
</p>
<br />

<p>
<img src="https://github.com/whitneydawson123/network-file-shares/assets/94804621/90c288a0-4354-497b-90db-1343916b70d4" height="80%" width="80%" alt="Step 2"/>
<img src="https://github.com/whitneydawson123/network-file-shares/assets/94804621/cf14feb3-55b6-42ee-86a2-5c4d8db23fc7" height="80%" width="80%" alt="Step 3"/>
<img src="https://github.com/whitneydawson123/network-file-shares/assets/94804621/66969726-b51b-4a2b-965e-965767f17235" height="80%" width="80%" alt="Step 4"/>
</p>
<p>
Right-click the folder, click properties, and hit the sharing tab. Then set the following permissions for each folder. <br/>
  
"read-access": group: "domain users", permission: "read" <br/>

"write-access": group: "domain users", permission: "read/write" <br/>

"no-access": group: "domain admins", permission: "read/write" <br/>

Skip the accounting folder for now.
</p>
<br />

<p>
<img src="https://github.com/whitneydawson123/network-file-shares/assets/94804621/18c7a03a-1284-42cd-8cc3-09ba26b6e38a" height="80%" width="80%" alt="Step 5"/>
<img src="https://github.com/whitneydawson123/network-file-shares/assets/94804621/c00b02b4-05f1-44ad-8c0c-10dc11be6633" height="80%" width="80%" alt="Step 6"/>
<img src="https://github.com/whitneydawson123/network-file-shares/assets/94804621/de49885e-eee8-4b7f-b6a7-a589c08a65fe" height="80%" width="80%" alt="Step 7"/>
</p>
<p>
Go to Client-1, then file explorer and search "\\dc-1" which will lead you to the shared folders. As a standard user you not be allowed to open the "no-access", you can open the "read-access" folder but cannot make a text document. You will be able to read and write in the "write-access" folder.
</p>
<br />

<p>
<img src="https://github.com/whitneydawson123/network-file-shares/assets/94804621/6344301c-cb0b-46f0-b829-3ce42dbf37a5" height="80%" width="80%" alt="Step 8"/>
<img src="https://github.com/whitneydawson123/network-file-shares/assets/94804621/8443c83b-6765-4dfe-ab2e-67ff96e8da04" height="80%" width="80%" alt="Step 9"/>
</p>
<p>
Go to DC-1, Active Directory Users and Groups, right-click mydomain.com, new, organizational unit, and make the name _SECURITY_GROUPS. <br/>
  
Within the _SECURITY_GROUPS, add a new group called "ACCOUNTING"
</p>
<br />

<p>
<img src="https://github.com/whitneydawson123/network-file-shares/assets/94804621/a0fd1d86-3aa3-4aa1-ba93-94cbd78d0479" height="80%" width="80%" alt="Step 10"/>
</p>
<p>
Add your standard user as a member of the accounting group and then set the permissions to read/write. 
</p>
<br />

<p>
<img src="https://github.com/whitneydawson123/network-file-shares/assets/94804621/babeb23b-cc8b-4ae9-b0b1-5869129a0ef3" height="80%" width="80%" alt="Step 11"/>
</p>
<p>
Go to your "accounting" folder and give permissions to everybody in the accounting group. If you reload your Client-1 machine. Go into the shared folders (\\dc-1) and open the accounting folder you should be able to read/write in the folder. Hope you enjoy this project!
</p>
<br />
