---
title: "Ubuntu 9.10: Broadcom NetXtreme BCM5761 not working"
date: 2009-11-30
forum: Networking &amp; Wireless
---

### Post by cybermac912 on 2009-11-30
I have an HP workstation with two network cards: An on-board NetXtreme BCM5764M, and a secondary NetXtreme BCM5761 in a PCIe slot. In Ubuntu 9.04, the secondary card worked fine (the network cable was plugged in there). After the upgrade to 9.10, that card stopped working, though the on-board card works. My colleague with an identical machine experienced the same thing.

The card appears to be there, it just won't acquire an IP address or anything. I even tried disabling the on-board card, but still nothing.

Output of sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5761 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 10
       serial: 00:10:18:4b:21:0c
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=5761-v3.68 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:54 memory:e3000000-e300ffff memory:e3010000-e301ffff memory:e3300000-e330ffff(prefetchable)
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth1
       version: 10
       serial: 00:24:81:a0:92:c2
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5764m-v3.35 ip=159.87.125.67 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:55 memory:e3100000-e310ffff
```

Can anyone give me some tips for troubleshooting?

Thanks
= Eric

---

### Post by Jouk on 2010-04-01
Hi Eric,

I'm in the same situation that you with the same hardware, none of my network cards is working.

Did you find a solution ?

Thanks.

---

### Post by cybermac912 on 2010-04-01
No, I didn't. I'm not at that job anymore, either, so it's sort of become a moot point for me :-/

---

### Post by yang on 2010-08-24
I'm also seeing this problem, on my Latitude 13. Any hints?

---

