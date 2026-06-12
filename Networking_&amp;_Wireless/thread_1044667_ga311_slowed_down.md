---
title: "ga311 slowed down"
date: 2009-01-19
forum: Networking &amp; Wireless
---

### Post by TekJunkie2k3 on 2009-01-19
I've recently upgraded my network adapter to a Netgear ga311. When I first installed the card everything was working fine and running at full speed. Lately I've been transferring files and I'm not going faster that 4-6 mbps.

> 
$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1e:2a:b6:34:08  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:2aff:feb6:3408/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13230610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6806075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 [COLOR="Red"]txqueuelen:1000 [/COLOR]
          RX bytes:2499676490 (2.4 GB)  TX bytes:467383457 (467.3 MB)
          Interrupt:22 Base address:0xc000 


It's listing it as 1000mbps, but my switch and transfer speeds say otherwise. I haven't made any changes to my settings since I've installed the card. I'm not really sure where to start. Thanks in advance.

---

