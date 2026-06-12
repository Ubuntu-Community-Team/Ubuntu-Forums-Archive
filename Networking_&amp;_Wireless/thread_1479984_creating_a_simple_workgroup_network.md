---
title: "creating a simple workgroup network"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by ikua on 2010-05-11
I am using an Ubuntu 64 bit desktop. I need to create a network (the way you create a workgroup in windoz). I have two other machines running Ubuntu also and all connected to a 3-Com switch through ethernet. I would prefer not to use DHCP, and just have a simple network where I can share resources like drives and printers.
Thanks in advance.

---

### Post by Iowan on 2010-05-11
Network Manager has the **link-local** option - or you can set up static addresses via NM.

---

### Post by ilikeyourflannel on 2010-05-11
Sounds like part of what you're looking for is file sharing in your local LAN.  For that you will need to use Samba.  [This]("http://www.debuntu.org/guest-file-sharing-with-samba") might be helpful.

To share printers you need CUPS.  If you want an easy way, aka GUI, to configure/manage your network look into webmin.

---

### Post by Iowan on 2010-05-11
[Here]("http://ubuntuforums.org/showthread.php?t=249889") is a help page for NFS - another option you might consider.

---

