---
title: "Slow Network Transfers with ipv6, samba, vstpd, e1000 driver"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by skaymakca on 2009-03-04
I have read many posts about ipv6 slowing things down but ran into an especially strange issue.

On an Ubuntu server 8.10 64 bit install, file transfers (over samba and vstpd) were at gigabit speeds to the system but pegged at about 9 mbit from the system. Testing 32 bit Ubuntu server and compiling drivers from intel for my nic (e1000 driver, Intel Pro 1000GT PCI) did not help.

Turning ipv6 (blacklisting the module) squashed the issue.  This was odd as even non ipv6 clients such as Win XP encountered the same problem (I  had the transfer issues with Win XP, Vista, Mac OS X Leopard, Ubuntu 8.10 Desktop 32 bit).

The system runs fine now.  Hope this helps someone else with the same issue.

---

