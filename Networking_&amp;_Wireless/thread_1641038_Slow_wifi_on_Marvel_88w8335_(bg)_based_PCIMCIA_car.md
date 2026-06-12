---
title: "Slow wifi on Marvel 88w8335 (b/g) based PCIMCIA card"
date: 2010-12-08
forum: Networking &amp; Wireless
---

### Post by roffik on 2010-12-08
Hi, I've got PCMCIA wifi card with Marvel 88w8335 chipset, and I use ndiswrapper to get it to work in Ubuntu. But when I connect to my wifi network (D-Link Di-524 b/g, wpa2 protected), the connection is very slow: about 100 kB/s, both upload and download. The download should be something about 12 Mb/s (which equals about 1.5 MB/s). Today I discovered that [FONT="Courier New"]lshw -C Network[/FONT] shows my card as [FONT="Courier New"]_wireless=IEEE 802.11b_[/FONT], and it should be 802.11b/_g_

```
*-network
       description: Wireless interface
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 1
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 03
       serial: 00:b0:8c:04:77:2d
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+mrv8335 driverversion=1.56+Marvell,02/22/2005,3.1.1.7 ip=192.168.0.11 latency=64 link=yes multicast=yes wireless=IEEE 802.11b
       resources: irq:11 memory:c4000000-c400ffff memory:c4010000-c401ffff

```

Could it be the reason why the speed is so low? How to change it?

---

