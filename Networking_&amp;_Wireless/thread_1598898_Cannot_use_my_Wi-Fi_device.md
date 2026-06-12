---
title: "Cannot use my Wi-Fi device"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by LeonPr20 on 2010-10-17
Hello there.
Lately, I've installed the latest version of Ubuntu - 10.10, on my laptop - Lenovo G530, and all work just fine but my Wi-Fi device. Ubuntu cannot even recognize that I have one (it tells that the firmware is missing). 
I have figured out that maybe I can fix this with the help of ndiswrapper, but it looks kind of tricky (especially if i don't have windows right now), and I searching for a simple way.
Hope for some usefull feedback :KS

---

### Post by LeonPr20 on 2010-10-17
Here is some information that can be usefull
(Updated)
 
>  
 
04:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 0
1)
Subsystem: Broadcom Corporation Device 04b5
Flags: bus master, fast devsel, latency 0, IRQ 18
Memory at f4700000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [40] Power Management version 3
Capabilities: [58] Vendor Specific Information: Len=78 <?>
Capabilities: [e8] MSI: Enable- Count=1/1 Maskable- 64bit+
Capabilities: [d0] Express Endpoint, MSI 00
Capabilities: [100] Advanced Error Reporting
Capabilities: [13c] Virtual Channel
Capabilities: [160] Device Serial Number 84-47-00-ff-ff-de-00-21
Capabilities: [16c] Power Budgeting <?>
Kernel driver in use: b43-pci-bridge
Kernel modules: ssb
 
 
07:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
Subsystem: Lenovo IdeaPad S10e
Flags: bus master, fast devsel, latency 0, IRQ 48
Memory at f4600000 (64-bit, non-prefetchable) [size=64K]
Expansion ROM at <ignored> [disabled]
Capabilities: [48] Power Management version 3
Capabilities: [50] Vital Product Data
Capabilities: [58] Vendor Specific Information: Len=78 <?>
Capabilities: [e8] MSI: Enable+ Count=1/1 Maskable- 64bit+
Capabilities: [d0] Express Endpoint, MSI 00
Capabilities: [100] Advanced Error Reporting
Capabilities: [13c] Virtual Channel
Capabilities: [160] Device Serial Number 00-23-5a-ff-fe-19-95-f3
Kernel driver in use: tg3
Kernel modules: tg3


---

### Post by GriffiN on 2010-10-19
the solution i found for that chipset and so as to be able to use b43 driver is the following

first

sudo apt-get remove --purge firmware-b43-installer

then

sudo apt-get install firmware-b43-lpphy-installer

worked inmediately

taken from:
[https://bugs.launchpad.net/ubuntu/+s...ey/+bug/655111](https://bugs.launchpad.net/ubuntu/+s...ey/+bug/655111)

---

