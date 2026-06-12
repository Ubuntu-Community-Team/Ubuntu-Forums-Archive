---
title: "HP DV6 (i5 Core) Wireless Doesn't Work"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by linux102 on 2010-09-19
Hi all,

I just bought an HP dv6-3033cl a week or two ago, and I'm having trouble getting wireless to work. Below is some possibly helpful info. I've tried un-blacklisting the ath_pci driver, but that didn't work. I also tried installing b4-fwcutter but that didn't work either.

Any help is appreciated. Thanks. :guitar:

root@ubuntu:~# lshw -C network
  *-network               
       description: Wireless interface
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:26:82:71:8a:09
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl1 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:16 memory:b3400000-b3403fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 60:eb:69:12:2d:fa
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:32 ioport:2000(size=256) memory:b1404000-b1404fff(prefetchable) memory:b1400000-b1403fff(prefetchable) memory:b1410000-b141ffff(prefetchable)


(I'm running 64 Bit 10.04 Ubuntu - installed through wubi)

---

