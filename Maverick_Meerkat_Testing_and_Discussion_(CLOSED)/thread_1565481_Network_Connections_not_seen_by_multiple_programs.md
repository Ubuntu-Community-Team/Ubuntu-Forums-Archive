---
title: "Network Connections not seen by multiple programs"
date: 2010-09-01
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by lachild on 2010-09-01
Hey Guys,

Anyone know why my teathered network connection is not being found by Evolution or Gwibber?

It's currently showing in ifconfig but network manager is not showing connected:

easytether0 Link encap:Ethernet  HWaddr 02:00:54:74:68:72  
          inet addr:192.168.117.2  Bcast:192.168.117.255  Mask:255.255.255.0
          inet6 addr: fe80::54ff:fe74:6872/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1855 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1765 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:1988313 (1.9 MB)  TX bytes:192884 (192.8 KB)


Also FireFox and Pidgin work fine, is it because they ignore Network Manager?  If so is there a way to get Evolution and Gwibber to do the same?

LaChild

---

### Post by lachild on 2010-09-01
Nevermind.  Installed Wicd and everythings fine now.

---

