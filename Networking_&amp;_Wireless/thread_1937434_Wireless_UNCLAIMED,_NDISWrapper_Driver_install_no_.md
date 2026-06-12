---
title: "Wireless UNCLAIMED, NDISWrapper Driver install no help"
date: 2012-03-07
forum: Networking &amp; Wireless
---

### Post by spacetimecowboy on 2012-03-07
Hi there,

Running 10.04 64bit on Acer 5733 with Atheros wireless chip.

Wireless not detected in Ubuntu, works in windows.

Followed troubleshooting advice and installed Atheros driver version 9.2.0.439 with NDISWrapper.

Current terminal readout for lshw -C network;

```

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: dc:0e:a1:1a:27:a7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=sb ip=192.168.1.82 latency=0 multicast=yes
       resources: irq:28 memory:d3400000-d340ffff
  *-network UNCLAIMED
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d2400000-d247ffff memory:d1400000-d140ffff(prefetchable)
```Reboot does not help.

Any advice?

Many thanks.

---

### Post by spacetimecowboy on 2012-03-17
Bump

Hey guys, any ideas?

Thanks

---

