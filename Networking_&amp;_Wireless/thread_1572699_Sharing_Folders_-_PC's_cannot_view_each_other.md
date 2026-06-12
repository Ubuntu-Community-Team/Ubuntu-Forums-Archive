---
title: "Sharing Folders - PC's cannot view each other"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by guv999 on 2010-09-11
Hi 
I am having some issues getting file sharing working on my network.
I am attempting to share files between two Ubuntu machines.
Neither machine can appear to see the other.
I have reviewed a number of threads and site helper guides, and so far can confirm:
[LIST]
[*]The machines can ping each other
[*]The IP addresses of each machine are static and firestarter firewall on both machines is set to allow incoming connections from the respective IP address.
[*]I have checked and appear to have downloaded all files required, and have enabled personal file sharing on both machines. 
I have selected the files I want to share
[*]When I attempt to access shared folders via Nautilus - entire network option all I see is the Windows network icon
[/LIST]
Any help greatly appreciated.

---

### Post by wyliecoyoteuk on 2010-09-11
Ah, but it is a windows network if you are using SMB
What happens if you double click the windows network icon?
Also, be aware that you will need the same samba users and passwords on both machines.

---

### Post by drdos2006 on 2010-09-11
Some more info for you which may be useful.
Server software on one machine, client software on the other.
> 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

Addendum:	On the Server machine
Needed to add Group of users on the machine designated as the server. Added the group via Webmin. If Webmin not an option then use terminal on the Server machine: 
sudo addgroup MyGroupName	
Added /media/sharedfiles on server with :	
sudo mkdir  /media/sdb1/sdb1-shared
Needed to change group permissions for /media/sdb1/sdb1-shared:	
sudo chgrp MyGroupName  /media/sdb1/sdb1-shared
//**
On the Client machine: Created a directory of /media/sharedfiles with : sudo mkdir /media/sharedfiles, mounted /media/sharedfiles from terminal as /media/sharedfiles with : 
sudo mount  <serverIPaddress>:/media/sharedfiles  /media/sharedfiles 
Can also be added to /etc/fstab for automatic mounting.
Copied files as test and it worked.

---

### Post by guv999 on 2010-09-12
Thank you for your help.   I have now managed to get things moving by using the 'connect to server' option on the client machine and entering the server IP address.

---

