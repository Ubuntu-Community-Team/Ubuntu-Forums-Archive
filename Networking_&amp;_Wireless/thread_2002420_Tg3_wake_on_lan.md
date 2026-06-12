---
title: "Tg3 wake on lan"
date: 2012-06-12
forum: Networking &amp; Wireless
---

### Post by sputnikuk on 2012-06-12
Hi all.

I've set each wakeup file in /sys/devices to enabled, have removed network-manager, set NETDOWN in /etc/init.d/halt to yes.  Ifconfig eth0 down is set in the rc.0 and rc.6 direcotories.  I've set ethtool  -s eth0 wol g.  Wol is enabled in the bios, i'm using the tg3 kernel module.  

Any ideas how to Wake on Lan?

Thanks, 
 Rob.

---

