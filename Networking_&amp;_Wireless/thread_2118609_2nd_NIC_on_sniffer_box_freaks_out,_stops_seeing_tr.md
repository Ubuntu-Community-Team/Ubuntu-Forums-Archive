---
title: "2nd NIC on sniffer box freaks out, stops seeing traffic"
date: 2013-02-21
forum: Networking &amp; Wireless
---

### Post by mbower on 2013-02-21
So I get notified that it stops seeing traffic, I go and look and find the below.  I suspect it could be a hardware issue, Im just not sure where to look.  I have checked logs (dmesg, syslog, etc) and haven;t found anything.

eth1      Link encap:Ethernet  HWaddr 68:05:ca:0e:3d:e9  
          UP BROADCAST RUNNING NOARP PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:164540197155032 errors:987241182428700 dropped:164540197071450 overruns:0 frame:658160788285800
          TX packets:164540197071450 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:164540251684148 (164.5 TB)  TX bytes:164540197071450 (164.5 TB)
          Interrupt:16 Memory:e1ac0000-e1ae0000

---

