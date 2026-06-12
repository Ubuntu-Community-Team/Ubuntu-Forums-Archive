---
title: "unable to install samba or smbfs"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by ranjith19 on 2009-04-27
I am running ubuntu 8.10

Whenever I try to install samba for sharing files this is what happens
please help 



[FONT="Lucida Sans Unicode"]root@master:/media/F-drive# apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
root@master:/media/F-drive# sudo apt-get install smbfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  smbfs: Depends: samba-common (= 2:3.2.3-1ubuntu3.4) but 2:3.2.3-1ubuntu3.5 is to be installed
E: Broken packages
[/FONT]

---

### Post by Iowan on 2009-04-27
*Might* need to update/upgrade existing packages first???

---

