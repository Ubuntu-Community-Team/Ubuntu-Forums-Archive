---
title: "wget working, but ping is not"
date: 2012-04-09
forum: Networking &amp; Wireless
---

### Post by darkdragon-001 on 2012-04-09
I can wget everything on the web but cannot ping it from my current ubuntu server machine [11.10]. I can even apt-get update/upgrade.

I can only ping in my local subnet.

I recently upgraded my ubuntu and afterwards the whole networking was broken. I am not fully sure what at least gave me most of the networking stuff back (creating some folders and symlinks).

Do you have any idea how to solve this problem?

Here is some more data:
```
route -n
```
> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.3.1     0.0.0.0         UG    100    0        0 eth0
192.168.3.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0



```
ifconfig eth0
```
> eth0      Link encap:Ethernet  HWaddr 00:0c:29:e2:27:b5
          inet addr:192.168.3.150  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fee2:27b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:285 errors:0 dropped:0 overruns:0 frame:0
          TX packets:386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:38882 (38.8 KB)  TX bytes:44011 (44.0 KB)
          Interrupt:18 Base address:0x2000

---

