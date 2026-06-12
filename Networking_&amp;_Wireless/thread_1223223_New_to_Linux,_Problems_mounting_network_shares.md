---
title: "New to Linux, Problems mounting network shares"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by pwsabm on 2009-07-25
I am new to Linux and Ubuntu. I am using the live cd version to try the version before installing on my laptop.
I am currently using mythbunt installation and it works fine, connected to the internet through my wireless router. On my home network I have a Windows Home Server and a ReadyNAS file server. I am unable to mount any of the shares on the. I installed pyNeighborhood and I can see them but can not mount anything. Samba is installed on the laptop I am using.
What am I doing wrong? how do I mount these shares and keep them mounted everytime the system restarts.

Thank you.

Pierre

---

### Post by superprash2003 on 2009-07-26
try this command sudo mount -t cifs //x.x.x.x/folder /mnt/folder -o username=user,password=passw0rd

fill in the require details..

---

