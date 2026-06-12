---
title: "configuring /etc/network/interfaces"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by argos3016 on 2010-03-06
How can I make a correct /etc/network/interfaces for the following ifconfig output:

eth0      Link encap:Ethernet  HWaddr 00:23:54:7e:2e:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:27 

eth1      Link encap:Ethernet  HWaddr 00:14:7f:50:f6:b9  
          inet addr:192.168.0.128  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::214:7fff:fe50:f6b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:171 errors:0 dropped:0 overruns:0 frame:0
          TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:91731 (91.7 KB)  TX bytes:25622 (25.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

ra0       Link encap:Ethernet  HWaddr 00:15:af:db:1b:d8  
          inet6 addr: fe80::215:afff:fedb:1bd8/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:54 errors:0 dropped:0 overruns:0 frame:0
          TX packets:481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6702 (6.7 KB)  TX bytes:0 (0.0 B)
          Interrupt:19 

__ Help

---

### Post by chili555 on 2010-03-06
May I assume you want eth1 to start automatically? By DHCP or with a static IP address? Is it wired or wireless? Have you removed Network Manager?

---

