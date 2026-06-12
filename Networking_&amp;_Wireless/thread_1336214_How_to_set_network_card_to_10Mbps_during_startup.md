---
title: "How to set network card to 10Mbps during startup"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by azhad on 2009-11-24
Hi All,

I am unable to use Ubuntu 9.10 due to being unable to downgrade the speed of my network card to 10Mbps. I tried to do it by making a script ["setethspeed10"]("http://ubuntuforums.org/showthread.php?t=903851") as mentioned in this forum earlier.

But the speed doesn't change. I have to manually type the mii-tool command in a terminal window whenever I start the computer (to use the network).

lspci:
Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)

Any ideas?

Thanks in advance.

---

### Post by chili555 on 2009-11-24
I suggest adding to */etc/rc.local*, just before 'exit 0':```
ethtool eth0 -s speed 10
```Please post back and let the searchers know the outcome.

---

