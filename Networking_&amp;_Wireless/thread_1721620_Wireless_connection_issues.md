---
title: "Wireless connection issues"
date: 2011-04-04
forum: Networking &amp; Wireless
---

### Post by jd3162 on 2011-04-04
Hey, sorry in advance, I think I've seen a couple other threads with this problem, but was never able to get my system running right by following instructions given there.
Anyway, just switched from Windows Vista to Ubuntu 10.10 on my Toshiba laptop and I'm loving it, except for some wireless connection problems. About 70% of the time, my computer is unable to find any wireless signals whatsoever, despite being right next to the router. When it does find the signal it connects fine and runs great, but most of the time it doesn't show any signals at all. I can't find any pattern to when it does or doesn't find the signal.

My result for the "sudo lshw -C network"

*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:1e:33:3c:3d:58
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.92 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:a000(size=256) memory:f8300000-f8300fff memory:80400000-8041ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:ed:4b:3d
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-28-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:f8200000-f820ffff
joshua@joshua-Satellite-A215:~$

---

### Post by jd3162 on 2011-04-05
Sorry to up this, I hope I'm not spamming... I just still have the issue. Would really love some help if anyone has any ideas

---

### Post by jd3162 on 2011-04-06
Please help. Still having the same problem. Any ideas would be welcome.

---

