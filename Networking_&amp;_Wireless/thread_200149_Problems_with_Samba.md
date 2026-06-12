---
title: "Problems with Samba"
date: 2006-06-19
forum: Networking &amp; Wireless
---

### Post by toLa` on 2006-06-19
Hi guys,

I've installed Windows XP Professional (with SP2) into a VMWare virtual machine. I've installed Samba onto Ubuntu 6.06, and have configured my samba.conf according to the instructions on [http://www.ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto](http://www.ubuntuforums.org/showthread.php?t=26438&highlight=samba+howto) .

I added  a user account on my Ubuntu installation named "samba", with the same password, and specified in my grub.conf the username map for the samba account.

"My Network Places" within Windows XP shows the Ubuntu server, and when double clicking it, i'm greeted with a username/password dialog, to which I entered samba/samba.

It wouldn't let me connect, returning the username/password dialog box again (meaning invalid un/pw?).

Can anyone provide a working how-to, or provide a working copy of their samba.conf and instructions on how to sucessfully create a smb account / specify a pw.

Cheers.

I've attached the screenshot taken showing what happens.

---

### Post by rbalfour on 2006-06-19
> 
 Configuring the Windows XP Client:

Notes : Only Windows XP-Professional Edition can join the Domain, it does not work for WindowsXP-Home Edition.

STEPS:

1) Make sure that the workstation belonged to the same workgroup as the server and have a fixed IP address and hostname assigned.

2) Change the registry entry, run the command regedt32 and do the below
a) RequireSignOrSeal Registry hack

HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\netlogon\parameters
"RequireSignOrSeal"=dword:00000000

b) Use the Registry Editor and edit the
HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\System\CompatibleRUPSecurity to have the DWORD value of 1

3) Use the Group Policy Editor (gpedit.msc) and enable "Computer Configuration\Administrative Templates\System\User Profiles\Do not check for user ownership of Roaming Profile Folders".

4) Go to MyComputer right click Properties. Go to Change and click on Domain and enter the domain-name you want to join. When joining the domain for the First time enter userid as root and give the samba password. Make sure there is an entry for the root in the smbpasswd (samba password) file.

5) Reboot and then the changes will be effective. 

Have you done the above?

---

### Post by toLa` on 2006-06-19
I'm not connecting to a domain --- does the above apply? I did the 1st 3 steps, except step 2b because it didn't exist in my registry.

---

### Post by rbalfour on 2006-06-19
I never used step 2b, so don't worry about that. Make sure you do step 2a. I know you  need this when sending UID/PWD to a samba server.

---

### Post by toLa` on 2006-06-19
Awesome, it works now, thanks vm :D

Again, Windows being the difficult party.

---

