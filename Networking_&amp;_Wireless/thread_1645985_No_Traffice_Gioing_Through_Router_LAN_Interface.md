---
title: "No Traffice Gioing Through Router LAN Interface"
date: 2010-12-15
forum: Networking &amp; Wireless
---

### Post by Geared on 2010-12-15
Hi all,

I have a router running Linux 2.4.26-tier-4801. It has two wireless interfaces.
The LAN interface is eth0 and the WAN interfaces are ath0 and ath1.
Router is running zebra routing software.

The main issue is that no traffic is transiting the LAN interface. I can't get any reason why that is happening yet it shouldn't be happening.

This is the output from ifconfig:

ath0      Link encap:Ethernet  HWaddr 00:15:6D:63:74:A4  
          inet addr:172.16.102.2  Bcast:172.16.102.3  Mask:255.255.255.252
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15586 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17369 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12680575 (12.0 MiB)  TX bytes:2648608 (2.5 MiB)

ath1      Link encap:Ethernet  HWaddr 00:15:6D:63:74:9C  
          inet addr:172.16.106.2  Bcast:172.16.106.7  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19917 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16101 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2820408 (2.6 MiB)  TX bytes:12731865 (12.1 MiB)

eth0      Link encap:Ethernet  HWaddr 00:0D:B9:03:6B:F8  
          inet addr:192.168.104.1  Bcast:192.168.104.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:24 dropped:0 overruns:0 frame:622
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:60 (60.0 b)  TX bytes:42 (42.0 b)
          Interrupt:10 

What is interesting is that the above router (A) is able to route traffic from router B whose interface particulars are below;


ath0      Link encap:Ethernet  HWaddr 00:15:6D:63:74:BE  
          inet addr:172.16.106.4  Bcast:172.16.106.7  Mask:255.255.255.248
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:735 errors:0 dropped:0 overruns:0 frame:0
          TX packets:818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:245216 (239.4 KiB)  TX bytes:127641 (124.6 KiB)

ath1      Link encap:Ethernet  HWaddr 00:15:6D:63:71:93  
          inet addr:172.16.126.1  Bcast:172.16.126.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4542 (4.4 KiB)  TX bytes:8066 (7.8 KiB)

eth0      Link encap:Ethernet  HWaddr 00:0D:B9:02:91:14  
          inet addr:192.168.126.1  Bcast:192.168.126.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:797 errors:0 dropped:0 overruns:0 frame:0
          TX packets:746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:96948 (94.6 KiB)  TX bytes:242942 (237.2 KiB)
          Interrupt:10

---

