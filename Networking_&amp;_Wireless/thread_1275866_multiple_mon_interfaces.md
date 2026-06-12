---
title: "multiple mon interfaces"
date: 2009-09-26
forum: Networking &amp; Wireless
---

### Post by equick on 2009-09-26
Hi! 

I was playing around with aircrack-ng and put my wireless card into monitor mode. However I think I've got it into a state now because when I run ifconfig, I have lots of interfaces prefixed with mon. Could someone tell me how to get rid of these please?

Thanks,

Ed.

mon0      Link encap:UNSPEC  HWaddr 00-0E-2E-75-54-B0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8888391 (8.8 MB)  TX bytes:0 (0.0 B)

mon1      Link encap:UNSPEC  HWaddr 00-0E-2E-75-54-B0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29911 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5552533 (5.5 MB)  TX bytes:0 (0.0 B)

mon2      Link encap:UNSPEC  HWaddr 00-0E-2E-75-54-B0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22903 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4332582 (4.3 MB)  TX bytes:0 (0.0 B)

mon3      Link encap:UNSPEC  HWaddr 00-0E-2E-75-54-B0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22857 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4328563 (4.3 MB)  TX bytes:0 (0.0 B)

mon4      Link encap:UNSPEC  HWaddr 00-0E-2E-75-54-B0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3963000 (3.9 MB)  TX bytes:0 (0.0 B)

mon5      Link encap:UNSPEC  HWaddr 00-0E-2E-75-54-B0-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7350 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1650676 (1.6 MB)  TX bytes:0 (0.0 B)

---

### Post by Iowan on 2009-09-26
Check */etc/network/interfaces*. If they aren't defined there, you may be able to find/clean them out of */etc/udev/rules.d/70-persistent-net.rules*.

---

