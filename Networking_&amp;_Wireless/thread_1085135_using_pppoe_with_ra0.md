---
title: "using pppoe with ra0"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by kilgore9 on 2009-03-02
I'm trying to set up a pppoe connection over wlan (ra0) with my dls modem.  In the Network Manager, the pppoe settings don't allow me to switch to ra0, only allows me to use eth0.  The wireless card is working, and is connected to the modem with a WEP key, but doesn't take the next step and connect using pppoe with my username and password from my ISP.  I tried using pppoeconf, which recognizes ra0 as existing, but it doesn't find the modem through ra0 even when my network manager says that its already connected to the modem.  
One solution might be to try using a wireless router....
But on my old computer (mac os) it was very simple changing pppoe over to wireless...why shouldn't it work with Ubuntu 8.04?  

I can connect with the ethernet plugged in just fine....

---

### Post by Crafty Kisses on 2009-03-02
First, what are the results of these commands?
```
lshw -C network
lspci
```
From there I or somebody else can help you further with your problem.

---

### Post by kilgore9 on 2009-03-02
(sorry i don't know how to quote)

**lshw -C network**

  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5764M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:1d:72:ef:fa:22
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5764m-v3.34 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: ra0
       version: 00
       serial: 00:24:2b:32:21:8b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless



**lspci**

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe (rev 10)
03:00.0 Network controller: RaLink Unknown device 0781
0d:06.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 01)
0d:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
0d:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 03)






Is that ok?

---

### Post by kilgore9 on 2009-03-05
bump!

Any ideas?

---

