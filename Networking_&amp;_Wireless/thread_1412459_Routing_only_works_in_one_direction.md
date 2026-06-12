---
title: "Routing only works in one direction"
date: 2010-02-21
forum: Networking &amp; Wireless
---

### Post by JuppS on 2010-02-21
Hallo at all,

I'm having a strange problem with my newly setup Ubuntu Server. The machine has two NICs with different network segments. Routing from one segment 1 to segment 2 works, but not the other way around. I don't get is...so here is my setup:

```

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:50:04:0c:a9:d1  
          inet addr:192.168.178.2  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:fe0c:a9d1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1753 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:167923 (167.9 KB)  TX bytes:155647 (155.6 KB)
          Interrupt:17 Base address:0x8c00 

eth1      Link encap:Ethernet  HWaddr e0:cb:4e:c6:b3:6e  
          inet addr:192.168.42.1  Bcast:192.168.42.63  Mask:255.255.255.192
          inet6 addr: fe80::e2cb:4eff:fec6:b36e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:341 errors:0 dropped:0 overruns:0 frame:0
          TX packets:435 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:10 
          RX bytes:42162 (42.1 KB)  TX bytes:41496 (41.4 KB)
          Memory:fbdc0000-fbde0000 

```

```

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.42.0    0.0.0.0         255.255.255.192 U     0      0        0 eth1
192.168.178.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.178.1   0.0.0.0         UG    0      0        0 eth0

```
As you can see, 192.168.178.1 is my gateway to the outside. The routing from net 192.168.178.0/24 into the other subnet works just fine, but routing from 192.168.42.0/26 into the other subnet does not work. What am I missing out? 

Oh, before I forget, the machines in net 192.168.42.0/26 have set the default gateway 192.168.42.1.

Jupp

---

