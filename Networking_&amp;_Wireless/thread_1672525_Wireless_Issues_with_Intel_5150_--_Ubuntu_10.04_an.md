---
title: "Wireless Issues with Intel 5150 -- Ubuntu 10.04 and Windows 7 on Dell Studio"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by AgentZeta on 2011-01-21
Hi All --

I am having extensive wireless issues with my computer. I have a Dell Studio 1737 with dual boot Windows 7 (32-bit) and Ubuntu 10.04. I have an Intel 5150 WiFi/WiMAX card that has been working fine since I got it (using it for WiFi, not WiMAX). Suddenly a couple months ago, the wireless stopped working, while I'm running either Windows or Linux, and neither will let me enable wireless. Windows tells me to turn on the wireless switch (which does nothing), and Linux won't let me click the "Enable Wireless" option. I had my computer looked at by Best Buy, and they told me that it is not a hardware issue, but a software one that has to do with the drivers, which I've reinstalled since, and no luck.

Does anyone have any advice/experience with this kind of issue?

Thanks,
AgentZeta

---

### Post by Bucky Ball on 2011-01-21
Welcome.

Sure sounds like hardware to me. Did it die in both OSs at the same time?

Could you run this in a terminal (Applications>Accessories>Terminal):

```
lspci
```Look for the line that starts 'Network Controller', probably somewhere near the bottom of the output and post it back here. If your wireless card is missing then the hardware is probably dead.

You can get more specific with:

```
lshw -C network
```

That will tell us the driver you're using and some other info.

---

### Post by AgentZeta on 2011-01-21
Thanks for the quick response.
Here's what I have from that:

> 04:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 5150 Series

From what I can tell, the hardware's there. I can see that from Ubuntu and from the Windows Device Manager as well.

Here's the rest of the lspci if you want it --


> 00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series]
04:00.0 Network controller: Intel Corporation WiMAX/WiFi Link 5150 Series
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)


Edit:
Here's the results from lshw:

>   *-network DISABLED      
       description: Wireless interface
       product: WiMAX/WiFi Link 5150 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:eb:07:28:b6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f8000000-f8001fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:22:19:ed:1c:ec
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v2.17 ip=10.26.23.168 latency=0 multicast=yes
       resources: irq:32 memory:fc100000-fc10ffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: wmx0
       serial: 00:1d:e1:04:d9:24
       capabilities: ethernet physical

---

