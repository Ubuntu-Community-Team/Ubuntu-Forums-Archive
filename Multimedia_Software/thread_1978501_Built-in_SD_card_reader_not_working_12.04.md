---
title: "Built-in SD card reader not working 12.04"
date: 2012-05-11
forum: Multimedia Software
---

### Post by escapologist on 2012-05-11
[SIZE=3]I am using Ubuntu 12.04 on a Advent 7109b/Uniwill L51II9.
  Tried 1 & 2 GB M2 cards (in both M2 duo & M2 adaptors) and a 2GB micro sd in adaptor and it will not see any of them although I know the cards work.
  The card reader is a O2 Micro 4-in-1 Media Card Reader: SD, MMC, MS, MSPro [/SIZE]

[SIZE=3]lspci returns the following:-[/SIZE]

  00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) 
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) 
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) 
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) 
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) 
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) 
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02) 
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02) 
06:04.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) 
[B]06:04.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01) 
06:04.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01) [/B]
06:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) 
[SIZE=2]
[SIZE=3]Looking at the results of 'sudo lshw' below, I am wondering if the  problem is with the 'UNCLAIMED' Mass Storage controller.........[/SIZE][/SIZE]

[B]*-generic
 description: SD Host controller             
 product: Integrated MMC/SD Controller 
 vendor: O2 Micro, Inc. 
 physical id: 4.2 
 bus info: pci@0000:06:04.2 
 version: 01             width: 32 bits             clock: 33MHz
 capabilities: pm cap_list
 configuration: driver=sdhci-pci latency=32
 resources: irq:18 memory:b0200800-b02008ff 

*-storage UNCLAIMED[/B] [B]
 description: Mass storage controller
 product: Integrated MS/xD Controller
 vendor: O2 Micro, Inc.
 physical id: 4.3
 bus info: pci@0000:06:04.3
 version: 01             width: 32 bits             clock: 33MHz
 capabilities: storage pm cap_list
 configuration: latency=32
 resources: memory:f0202000-f0202fff     [/B]

[SIZE=3]It would seem like this has been an  ongoing problem from previous versions of Ubuntu, so I'm hoping there is  an easy fix out there, I just need to find it.
I know this is similar to other posts, but I cannot see one that has  been confirmed as solved (forgive me if this is not accurate!)

    Thanks in advance - any help or advice would be greatly appreciated. [/SIZE][SIZE=3]):P[/SIZE]

---

