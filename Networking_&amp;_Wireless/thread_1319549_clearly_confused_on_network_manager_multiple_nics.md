---
title: "clearly confused on network manager multiple nics"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2009-11-08
what is the difference between local link only and shared among all computers?
when i select shared among computers, it just does not work, nm applet goes crazy.
the only thing that works for me is local link only.
is there a way to pass internet thru to the other nic card?

> scott@scott-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:22:15:54:fa:a6  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fe54:faa6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4786 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5186 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:3770397 (3.7 MB)  TX bytes:998393 (998.3 KB)
          Interrupt:28 

eth1      Link encap:Ethernet  HWaddr 00:10:5a:73:c4:83  
          inet addr:169.254.8.189  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::210:5aff:fe73:c483/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8056 (8.0 KB)  TX bytes:80932 (80.9 KB)
          Interrupt:16 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:872 errors:0 dropped:0 overruns:0 frame:0
          TX packets:872 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1410095 (1.4 MB)  TX bytes:1410095 (1.4 MB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.174.1  Bcast:172.16.174.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.110.1  Bcast:192.168.110.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

scott@scott-desktop:~$ 


---

