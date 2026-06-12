---
title: "Unable to connect to hidden wireless network"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by dejies on 2009-05-13
Hi all,
I am new to ubuntu, Yesterday i installed ubuntu 9.04 ,on my dell insprion 1525 .
Built in  wireless card is BCM4312 802.11b/g from Broadcom Corporation.The strange thing is i am able to connect to an open wireless network(not hidden).But when i try to connect to a hidden network it fails,My wireless security is WPA$WPA2 Personal.
Also when i go to System->Administration->Hardware Drivers i can see Broadcom STA Wireless Driver with status Active .Can any one help me to fix my issue.

MY ifconfig shows

eth0      Link encap:Ethernet  HWaddr 00:21:9b:f1:0c:45  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:30 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2926 (2.9 KB)  TX bytes:4645 (4.6 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:23:4d:a9:4b:e6  
          inet addr:192.168.15.3  Bcast:192.168.15.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fea9:4be6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26693 errors:0 dropped:0 overruns:0 frame:19024
          TX packets:17371 errors:27 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37756683 (37.7 MB)  TX bytes:1801641 (1.8 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3345 (3.3 KB)  TX bytes:3345 (3.3 KB)


Thanks 
Dejies

---

