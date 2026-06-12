---
title: "Can't see Wireless Networks [11.04, BCM4312]"
date: 2011-09-30
forum: Networking &amp; Wireless
---

### Post by ani-fail on 2011-09-30
As the title suggests. I can't see any available wireless networks. I checked for updates and updated the drivers using System > Admin > Additional Drivers. Everything appears kosher, the additional drivers window says my drivers are activated and in use,  I checked rfkill and nothing is being blocked. I'm pretty new to ubuntu so I don't know where to go from here.

**lshw -C network:**
```

  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:b2:b0:26
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:40:0b:5d
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=half firmware=N/A ip=169.233.40.78 latency=0 link=yes multicast=yes port=twisted pair speed=10Mbit/s
       resources: irq:45 memory:f68fc000-f68fffff ioport:de00(size=256)

```More info can be provided.

---

### Post by garvinrick4 on 2011-09-30
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
Open synaptic type b43 in search window install what I have checked off.
Make sure nothing else b43 (or bcm type bcm in search window to check) installed install with wired connection remove wired reboot.

---

