---
title: "eth0 won't initialise after upgrading to 11.10"
date: 2012-03-26
forum: Networking &amp; Wireless
---

### Post by Jammie001 on 2012-03-26
On my media server I decided to upgrade from 11.04 to 11.10 to get ready for the coming 12.04 release, but now networking wont initialise correctly.

So I boot into recovery mode, run fsck and drop into the shell. Basically when I run ifconfig there is an ipv6 address, but no ipv4 address. To fix this I have to manually run "/etc/init.d/networking restart" and it works from there, but on reboot it wont initialise correctly. Has anyone got any suggestions?

---

