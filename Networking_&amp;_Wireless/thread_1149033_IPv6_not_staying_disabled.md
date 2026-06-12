---
title: "IPv6 not staying disabled"
date: 2009-05-04
forum: Networking &amp; Wireless
---

### Post by iamkion132 on 2009-05-04
I'm either following directions wrong or have misread something along the way.  I've edited the alias. file and have blacklist IPv6.  Here is the output for my ifconfig.  I can post the contents of my alias. and blacklist file if I need to. 

owner@owner-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1f:3a:0e:b4:ac  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3aff:fe0e:b4ac/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110283 errors:0 dropped:0 overruns:0 frame:231607
          TX packets:102124 errors:9 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:117888993 (117.8 MB)  TX bytes:19484260 (19.4 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:1d:09:a5:26:9a  
          inet6 addr: fe80::21d:9ff:fea5:269a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:f9bfe000-f9c00000

---

