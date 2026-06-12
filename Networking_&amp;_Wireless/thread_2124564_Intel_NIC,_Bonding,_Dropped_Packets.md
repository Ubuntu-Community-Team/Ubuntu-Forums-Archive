---
title: "Intel NIC, Bonding, Dropped Packets"
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by Xanko on 2013-03-11
Xubuntu 12.04 Precise with Kernel Version 3.5.0-21-generic

I am having some minor issues with networking. To start I was having a lot of dropped packets causing stuttering during SSH sessions to my server and network applications would lag. I finally (mostly) fixed that issue by upgrading the e1000e driver for the NIC (Intel 82574L) to the latest version (2.2.14 from 2.0). I still have dropped packets however there is not nearly as many dropped packets as I had previously (SSH does not stutter and the net applications are working again).

The new issue is that I use the Intel card (eth2) bonded with another network card (eth1) for backup. The backup interface should not be used however it is showing all the dropped packets (this behavior was the same prior to the driver update)

```
bond0     Link encap:Ethernet  HWaddr 00:11:11:be:7e:e1            inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:11ff:febe:7ee1/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:1604478 errors:0 dropped:7417 overruns:0 frame:0
          TX packets:30100808 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123181521 (123.1 MB)  TX bytes:44505542597 (44.5 GB)


eth1      Link encap:Ethernet  HWaddr 00:11:11:be:7e:e1  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:22971 errors:0 dropped:7417 overruns:0 frame:0
          TX packets:142069 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1789819 (1.7 MB)  TX bytes:209803384 (209.8 MB)


eth2      Link encap:Ethernet  HWaddr 00:11:11:be:7e:e1  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:1581507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29958739 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:121391702 (121.3 MB)  TX bytes:44295739213 (44.2 GB)
          Interrupt:18 Memory:fbbe0000-fbc00000 
```

Is this normal behavior or a bug? I don't think I have ever experienced dropped packets, certainly not on the local network.

---

