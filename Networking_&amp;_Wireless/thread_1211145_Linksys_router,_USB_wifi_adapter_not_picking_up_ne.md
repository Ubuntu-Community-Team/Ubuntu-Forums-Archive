---
title: "Linksys router, USB wifi adapter not picking up networks"
date: 2009-07-12
forum: Networking &amp; Wireless
---

### Post by HarryG321 on 2009-07-12
I've got a USB Wireless Internet Adapter for my computer and it picks up 4 wireless networks on windows vista, but when I boot Linux [v.9.04], it can't pick up any. I tried switching to WICD, but still no luck.


```
sudo lshw -C
```

network

*-network 

description: Ethernet interface

product: 82562V-2 10/100 Network Connection

vendor: Intel Corporation
physical id: 19

bus info: pci@0000:00:19.0
logical name: eth0

version: 02
serial: 00:1a:a0:8e:3f:39

capacity: 100MB/s
width: 32 bits
clock: 33MHz

capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation

configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair
*-network DISABLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 26:6b:93:5a:db:b5
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes




```
lsusb
```


Bus 001 Device 004: ID 0416:0035 Winbond Electronics Corp. W89C35 802.11bg WLAN Adapter

---

