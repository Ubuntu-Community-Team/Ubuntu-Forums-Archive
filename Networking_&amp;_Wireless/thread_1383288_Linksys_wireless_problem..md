---
title: "Linksys wireless problem."
date: 2010-01-17
forum: Networking &amp; Wireless
---

### Post by tdawg2k7 on 2010-01-17
I'm currently dual-booting Windows 7 and ubuntu 9.10 karmic koala x64.

I'm trying to connect to my home wireless network with my Linksys wmp54G pci card but Ubuntu isn't automatically recognizing the card and connecting.

I'm also not able to use a wired connection with this machine, only wireless. Which is why I haven't been able to try ndiswrapper. 

Linux is pretty new to me by the way.

This also might be helpful...



```
sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: 88E8053 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:17:31:f3:3d:91
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:dfdfc000-dfdfffff ioport:c800(size=256) memory:dfdc0000-dfddffff(prefetchable)
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:04:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:19 memory:dfffe000-dfffffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:10:e5:53:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

---

### Post by tdawg2k7 on 2010-01-17
Ok, so I did get ndiswrapper installed from the ubuntu cd but when I tried the linksys drivers I got "Hardware Not Present" in a dialogue box although in the ndiswrapper window under the driver name it said "Hardware Present: Yes". But still no network connection yet.

---

### Post by northd_tech on 2010-02-21
> **tdawg2k7 said:**
> 
**sudo lshw -c network**
  *-network               
       description: Ethernet interface
       product: **88E8053 PCI-E Gigabit** Ethernet Controller
       vendor: **Marvell Technology Group** Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 15
       serial: 00:17:31:f3:3d:91
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:29 memory:dfdfc000-dfdfffff ioport:c800(size=256) memory:dfdc0000-dfddffff(prefetchable)
  *-network
       description: Network controller
       product: BCM**4318** [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: **Broadcom** Corporation
       physical id: 7
       bus info: pci@0000:04:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:19 memory:dfffe000-dfffffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1c:10:e5:53:41
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

That cabled ethernet adapter is actually a Marvell **88E8053**, so I don't expect Linksys drivers to work.  The wireless is a Broadcom 4318, and a forum search will find many threads about that here.

---

