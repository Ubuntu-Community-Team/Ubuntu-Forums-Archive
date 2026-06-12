---
title: "Atheros AR5212 unclaimed in 11.10"
date: 2011-10-17
forum: Networking &amp; Wireless
---

### Post by Darkwing87 on 2011-10-17
I upgraded to 11.10 last week rebooted and my wireless card worked. When I turned the computer on the following day my card was unclaimed.

sudo lshw -c network gives me 
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 1c:6f:65:ad:2a:54
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.0.105 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:ce00(size=256) memory:fdfff000-fdffffff memory:fdff8000-fdffbfff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5212/AR5213 Multiprotocol MAC/baseband processor
       vendor: Atheros Communications Inc.
       physical id: 6
       bus info: pci@0000:04:06.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
       resources: memory:fdce0000-fdcfffff

```
I ran into this problem once before on 11.04 but not sure how/if I fixed it. Any help would be awesome.

---

