---
title: "Can ping but can't browse..."
date: 2010-09-21
forum: Networking &amp; Wireless
---

### Post by Beanmonster on 2010-09-21
This question has been asked numorous times but I cannot find a solution anywhere, I am desperate for any help.

I have a DSL modem connected to the net, I can successfully browse without trouble on 3 network computers.

My desktop-pc (ubuntu 10.04.1) however, can successfully PING hostnames but nothing in the application layer can access the net!

route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
```

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:25:11:02:63:f1  
          inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:11ff:fe02:63f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:3114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4931 errors:0 dropped:0 overruns:0 carrier:15
          collisions:0 txqueuelen:1000 
          RX bytes:435792 (435.7 KB)  TX bytes:462377 (462.3 KB)
          Memory:febc0000-fec00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:35813 (35.8 KB)  TX bytes:35813 (35.8 KB)
```

[LIST]
[*]**IPTABLES** are empty
[*]*Traceroute* succeeds
[*]**IPv6** globally disabled
[*]_MTU_ adjustment has no effect
[*]_/etc/resolv.conf_ - DNS resolving successfully
[/LIST]

I have no idea what to do, thanks for any advice.

---

