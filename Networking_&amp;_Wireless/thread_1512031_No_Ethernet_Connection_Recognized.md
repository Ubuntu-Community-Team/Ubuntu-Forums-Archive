---
title: "No Ethernet Connection Recognized"
date: 2010-06-17
forum: Networking &amp; Wireless
---

### Post by adsum01nl on 2010-06-17
Hi, 
I am new to Ubuntu having come from a different distro. I just installed 10.04 on my new netbook and I am suprised to see that the ethernet is not recognized. When I run```
ifconfig eth0
``` the result is ```
no such device
``` The machine was working fine before I installed Ubuntu. I am suprised to see this problem as I have already installed it on a few machines without any problem such as this. Your help would be very much appreciated for finding out what happened to my ethernet.

---

### Post by Iowan on 2010-06-17
Check (post?) **sudo lshw -C network** - seems like drivers are frequently an issue...

---

### Post by The Low End Theory on 2010-06-19
i have the same problem except with wlan0,

sudo lshw -C network returns
```
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:c3:91:58
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=5751-v3.29a latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:dfdf0000-dfdfffff
  *-network
       description: Network controller
       product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:dfcfe000-dfcfffff

```

everything had been working fine for the past week or so, but this morning when i turned on my laptop it wasnt working

---

