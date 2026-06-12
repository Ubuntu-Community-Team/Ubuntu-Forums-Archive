---
title: "how connect to intenet via NAT?"
date: 2011-02-28
forum: Networking &amp; Wireless
---

### Post by aminzadenoori on 2011-02-28
hi.i'm using ubuntu 8.04(guset)on windows 7(host)with vmware6.5 as server.i want to share network connection via NAT.so any body can help me ?

---

### Post by An Sanct on 2011-02-28
I don't know about vmware, but in VirtualBox, there is a setting for the network card of the guest, there you can set NAT and that does the trick ...

[This article here]("http://www.virtuatopia.com/index.php/VMware_Server_NAT_Configuration") says:

> **Configuring NAT on Linux Hosts **

 Unfortunately, VMware Server on Linux currently lacks a user friendly  equivalent of the Windows Manage Virtual Networks tool, instead  requiring the manual editing of the */etc/vmware/vmnet8/nat/nat.conf*  file (keeping in mind that the vmnet8 name will need to be changed if  the settings are to be configured for a custom created virtual network). 
The *nat.conf* file contains a number of different sections, each allowing a different aspect of the NAT device to be configured: 


---

