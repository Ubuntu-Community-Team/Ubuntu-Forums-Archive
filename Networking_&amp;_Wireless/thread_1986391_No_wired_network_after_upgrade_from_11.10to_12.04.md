---
title: "No wired network after upgrade from 11.10to 12.04"
date: 2012-05-24
forum: Networking &amp; Wireless
---

### Post by bdalzell on 2012-05-24
I installed ubuntu studio 11.10 in my older Athlon to get an XFCE system.
Live DVD found wired connection and installation found wired connection
The ethernet device is a Broadcom NetXtreme BCM5788 Gigabite ethernet.

When I did the upgrade to 12.04 the system lost its ethernet connection and I have not been able to figure out how to restore it. The entry for the Broadcom connection is ghosted out when the connection icon at the topof the screen is clicked on. I also had no internet when I previously tried to install Ubuntu-studio 12.04 directly from DVD but that installation failed - I suspect because of the lack of online connectivity. The inability to get online when I did the upgrade from 11.10 only came on the reboot into 12.04.

---

### Post by Wizman66 on 2012-06-07
I am having the same problem. Internet was working with 11.10 but stopped working after upgrading to 12.04. internet will only work when I created the fite /etc/resolv.conf with the dns nameserver IP, however this file gets over written everytime I reboot. found out that in Ubuntu 12.04  \etc\resolv.conf file is a symlink to a file inside the resolvconf folder

---

### Post by graphius on 2012-06-24
So is there a permanent solution to this?
I am not having the issue with my mint box.

---

