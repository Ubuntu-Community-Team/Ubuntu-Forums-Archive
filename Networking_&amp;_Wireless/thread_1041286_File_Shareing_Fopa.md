---
title: "File Shareing Fopa"
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by beilzabub on 2009-01-16
I initially started fileshareing between my laptop (windows xp) and my desktop(ubuntu 8.10) I transfered some files off of my laptop and installed ubuntu on it. When ever I try to access my network it takes about 1min to load and it will always come up blank. On my desktop i can see the files i am sharing with it and I can see my laptop but when i try to access the files it does the same thing that the laptop does when it is trying to connect.

I ran an ifconfig on both comps.

cory@cory-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:11:d0:24:c5  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:fed0:24c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33230 (33.2 KB)  TX bytes:11234 (11.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3752 (3.7 KB)  TX bytes:3752 (3.7 KB)

=========================================================================

killmonky07@killmonky07-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:01:4a:ef:e1:76 
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:4aff:feef:e176/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1513 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1970 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1226483 (1.2 MB)  TX bytes:373259 (373.2 KB)

eth1      Link encap:Ethernet  HWaddr 00:16:6f:07:40:7f 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0x2000 Memory:b0106000-b0106fff

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2936 (2.9 KB)  TX bytes:2936 (2.9 KB)


Any ideas or anything would be extremely helpful.

---

