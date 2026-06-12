---
title: "Can't get wired or wireless to work"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by perezo89 on 2010-09-09
Hello!
I have installed Ubuntu 9.10 twice on two different laptops that had wireless cards that weren't working until I sudo apt-get update(d) them. After that, the wireless cards seem to miraculously work. But I was able to download them because they had working ethernet cards.
I'm working on a new laptop (Dell Inspiron 1150). I installed Ubuntu 9.10 like normal but I could not get a wired connection. I plugged in directly to my modem and it still cannot connect at all. It says that Auto eth0 is available, but it tries to connect but can't seems to make it. I downgraded to 9.04 to see if there was any changes, and there aren't. The same problem persists. Anyone know how to solve this problem? What's my next step to troubleshoot?

ifconfig:
```

eth0        Link encap:Ethernet HWaddr 00:11:43:6d:4b:0d
              inet6 addr: fe80::211:43ff:fe6d:4b0d/64 Scope:Link
              UP BROADCAST RUNNING MULTICAST  MTU:1500 Metric:1
              RX packets:1503 errors:0 dropped:0 overruns:0 frame:0
              TX packets:19 errors:0 dropped:0 overruns:0 frame:0
              collisions:0 txqueuelen:1000
              RX bytes:457789 (457.7 KB)  TX bytes:4990 (4.9 KB)
              Interrupt:7

lo           Link encap:Local Loopback
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:92 errors:0 dropped:0 overruns:0 frame:0
              TX packets:92 errors:0 dropped:0 overruns:0 frame:0
              collisions:0 txqueuelen:0
              RX bytes:7216 (7.2 KB)  TX bytes:7216 (7.2 KB)
```lshw -C Network:

```

*-network:0                
description: Ethernet interface
product: BCM4401 100Base-T
vendor: Broadcom Corporation
physical id: 1
bus info: pci@0000:02:01.0
logical name: eth0
version: 01
serial: 00:11:43:6d:4b:0d 
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
 
 *-network:1
description: Network controller   
product: BCM4306 802.11b/g Wireless LAN Controller
vendor: Broadcom Corporation 
physical id: 2
bus info: pci@0000:02:02.0
version: 03  
width: 32 bits  
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=32 module=ssb
  
*-network:0 DISABLED    
description: Wireless interface
physical id: 2
logical name: wlan0
serial: 00:0b:7d:17:6e:fc
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  
*-network:1 DISABLED
description: Ethernet interface
physical id: 3
logical name: pan0
serial: da:17:0f:79:d7:37
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 
firmware=N/A multicast=yes
```

---

### Post by perezo89 on 2010-09-09
Also, is it possible to download the same things apt-get update downloads on a windows computer and transfer the files and/or packages to ubuntu? Or is it strictly only accessible through Ubuntu?

---

