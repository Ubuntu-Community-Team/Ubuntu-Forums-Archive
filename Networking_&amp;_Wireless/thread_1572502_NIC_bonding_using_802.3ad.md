---
title: "NIC bonding using 802.3ad"
date: 2010-09-11
forum: Networking &amp; Wireless
---

### Post by bailong on 2010-09-11
Hi there,

I've configured 2 NICs for bonding using LACP, but traffic is going over one NIC only:

```

bailong@apollo:~$ ifconfig 
bond0     Link encap:Ethernet  HWaddr 00:1d:7d:09:8b:e0  
          inet addr:10.100.0.101  Bcast:10.100.255.255  Mask:255.255.0.0
          inet6 addr: fe80::21d:7dff:fe09:8be0/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:37764013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39725170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37822531889 **(37.8 GB)**  TX bytes:41877178152 **(41.8 GB)**

eth0      Link encap:Ethernet  HWaddr 00:1d:7d:09:8b:e0  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:2378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:462854 **(462.8 KB)**  TX bytes:86837 **(86.8 KB)**
          Interrupt:31 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:1d:7d:09:8b:e0  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:37761635 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39724140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37822069035 **(37.8 GB)**  TX bytes:41877091315 **(41.8 GB)**
          Interrupt:32 Base address:0x4000 

```

Bonding seems to be configured correctly:

```
bailong@apollo:~$ cat /proc/net/bonding/bond0 
Ethernet Channel Bonding Driver: v3.5.0 (November 4, 2008)

Bonding Mode: IEEE 802.3ad Dynamic link aggregation
Transmit Hash Policy: layer2 (0)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0

802.3ad info
LACP rate: slow
Aggregator selection policy (ad_select): stable
Active Aggregator Info:
	Aggregator ID: 1
	Number of ports: 2
	Actor Key: 17
	Partner Key: 1006
	Partner Mac Address: f4:ac:c1:28:8b:55

Slave Interface: eth0
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:1d:7d:09:8b:e0
Aggregator ID: 1

Slave Interface: eth1
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:1d:7d:09:91:18
Aggregator ID: 1

```

Any idea why the traffic is not going over both interfaces?

---

### Post by mdfakkeer on 2011-11-16
I am also facing same problem. If any body know to solve the issue please help.

---

