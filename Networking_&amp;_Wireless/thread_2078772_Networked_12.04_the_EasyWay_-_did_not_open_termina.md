---
title: "Networked 12.04 the EasyWay - did not open terminal but once"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by Rezliw on 2012-10-31
However, only after a lost weekend where I finally trashed everything, saved any important data and reinstalled Ununtu 12.04 LTS.  Went to my Mac OS computer to see how things worked.

1. Install Ubuntu
2. Open router configuration and reserve IP  and mac address for all computers (Turn them all on and look at attached devices in Netgear or something to that effect in others) then copy and paste mac address and reserve IP s for all devices including your print server if you have one.
* See below
3. Create folder you want to share, then right click and share, will get a message to install samba - OK install
4.  Open terminal  sudo nano /etc/samba/smb.conf  (or use whatever editor you want)  The ^ in nano means "ctrl" key
5.  Change WORKGROUP= to your windows workgroup, MSHOME or what ever you have named it (Rt click My Computer, properties in Windows computer to look at computer name and see workgroup name-or set up one by changing computer name if needed)  In Nano Ctrl X and "Y" and save smb.conf
6.  In Ubuntu, click file, open "Connect to Server" enter the the IP of the computer you want to look for shared folders in or the router IP address for the \\Readyshare USB and then use the dropdown to select "Windows Share"  then click connect and BAM, the folders come up and stay in your network section of files until you shut down or eject.  You probably can figure out how to make them stay but who wants all that clutter when you don't need it.

*Add your print server, if you have one before installing samba, don't samba the print server.  Add printer and it will find the print server.
.
.:guitar:

---

