---
title: "Intel PRO/1000 MT Adapter TX"
date: 2010-05-29
forum: Networking &amp; Wireless
---

### Post by helfrez on 2010-05-29
Anyone have clues or tweaks to possibly get an Intel Pro/1000 up to speed. Using iperf, I can fairly easily sustain 700-800 Mbits/sec Rx, however, my TX seems to be stuck at 335 Mbit/sec. Enabling jumbo frames didn't help much. I also tried a few sysctl.conf window tweaks, but nothing seems to have any effect on Tx. Only one interface is up at the moment, I intend to bond the interfaces via 802.3ad if I can get the Tx issue sorted.

Ubuntu 10.04 AMD64
Kernel:  2.6.32-21-server
01:0a.0 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
01:0a.1 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)


Tx
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    392 MBytes    329 Mbits/sec

Rx
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.1 sec    906 MBytes    752 Mbits/sec

---

### Post by bferd on 2011-03-07
Try reading this? Hope it helps.

[http://manpages.ubuntu.com/manpages/maverick/en/man4/em.4freebsd.html](http://manpages.ubuntu.com/manpages/maverick/en/man4/em.4freebsd.html)

---

