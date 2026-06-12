---
title: "Set Up Networking for file transfer between Ubuntu Desktop and Mandriva Laptop"
date: 2009-07-21
forum: Networking &amp; Wireless
---

### Post by Canis familiaris on 2009-07-21
I just purchased a Switch, which is connected to a WAN Router, Desktop and Laptop. Internet works fine on both, however I was wondering how to facilitate data transfer i.e LAN b/w two PCs. Desktop has Ubuntu, Laptop has Mandriva. (A distro neutral approach would be appreciated since I also use Arch in the desktop)
I am n00b in networking, so an easy approach would be appreciated.

---

### Post by prshah on 2009-07-21
> **Canis familiaris said:**
> I just purchased a Switch, which is connected to a WAN Router, Desktop and Laptop. Internet works fine on both, however I was wondering how to facilitate data transfer i.e LAN b/w two PCs. Desktop has Ubuntu, Laptop has Mandriva. (A distro neutral approach would be appreciated since I also use Arch in the desktop)
I am n00b in networking, so an easy approach would be appreciated.

Considering that you are using Arch, I will assume that you are familiar with the command line and accordingly give pointers. However, if you need more details at any point, post back for detailed commands and step-by-steps.

If you are only looking for casual transfers on a rare / occasional basis, you are best off with an ssh server running on any one system, and using scp (secure ftp) to transfer files in either direction. Use:```
sudo apt-get install openssh-server
``` Relevant settings will be in /etc/ssh/sshd_config.

If you are looking at streaming and/or other home networking, you should look at setting up an NFS (network file system) on the system you would designate as a server. Use: ```
sudo apt-get install nfs-kernel-server
``` Relevant config options are in /etc/nfs

If you are looking for all-round home networking with "alternate" operating systems (ok, I'll just say it: Windows) then you can setup a Samba-based network. Use```
sudo apt-get install samba
``` on each computer; you will need a restart after installation (at least a re-login) to use samba features.

Post back if you need more details on any of these.

---

### Post by Canis familiaris on 2009-07-21
^ ^ ^
Thanks. NFS was set and I transferred from Laptop to Desktop.

However I have a problem. 
I can't ping to the laptop from the desktop while I can ping from laptop to desktop. Why is that happening? Is a Port blocked in Mandriva?

---

### Post by Canis familiaris on 2009-07-21
Sorted it out. It was a Firewall issue. Set up NAS too. :)
Thank you prshah

---

