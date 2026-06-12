---
title: "Broadcom BCM4312 DISABLED"
date: 2010-09-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jmpeer on 2010-09-18
Hey, I installed Ubuntu 10.10, and my wireless card isn't functioning. I tried installing the package b43-fwcutters, the package bcmwl-kernel-source, and Broadcom's Linux STA driver directly from their site, but none of them help. 

From the command 'sudo lshw -C network', I get:
(I thought 'wlan0' is supposed to describe the Broadcom card like 'etho0' described the Realtek card, and I suppose '*-network DISABLED' is a problem...)
```

  *-network
       
description: Network controller
      
 product: BCM4312 802.11b/g
      
 vendor: Broadcom Corporation
       
physical id: 0
       
bus info: pci@0000:03:00.0
       
version: 01
       
width: 64 bits
       
clock: 33MHz
       
capabilities: pm msi pciexpress bus_master cap_list
      
 configuration: driver=b43-pci-bridge latency=0
       
resources: irq:17 memory:f0100000-f0103fff
  

*-network
      
 description: Ethernet interface
       
product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       
physical id: 0
       
bus info: pci@0000:04:00.0
      
 logical name: eth0
      
 version: 02
       
serial: 00:24:e8:de:a4:5e
       
size: 10MB/s
       
capacity: 100MB/s
       
width: 64 bits
       
clock: 33MHz
      
 capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
      
 configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
      
 resources: irq:27 ioport:2000(size=256) memory:f0510000-f0510fff(prefetchable) memory:f0500000-f050ffff(prefetchable) memory:f0520000-f053ffff(prefetchable)
  

*-network DISABLED
      
 description: Wireless interface
       
physical id: 2
       
logical name: wlan0
       
serial: 00:22:5f:fc:bb:39
       
capabilities: ethernet physical wireless
       
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


```

---

### Post by kerry_s on 2010-09-18
in 10.10 it's firmware-b43-installer, use that search in synaptic, type "b43".

---

### Post by cariboo on 2010-09-18
You're trying to use the wrong driver, the bcm4312 chipset uses the wl driver, it should be available through System->Administration->Additional Drivers, it will be listed as STA. If you don't have a network cable, the drivers are on the Live CD. Look for bcmwl-kernel-source. Make sure you have build-essentials installed before trying to install the driver, they are also on the Live CD.

---

### Post by jmpeer on 2010-09-18
Ah, now that I found an ethernet cord, it cleared up real fast. I just needed basic stuff like build-essentials. Thanks for the replies.

---

