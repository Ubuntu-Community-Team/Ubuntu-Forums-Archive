---
title: "Set up a wireless connection"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by PECHAS on 2009-12-31
Hello,

I would like to receive some help to set up a wireless connection on Ubuntu, what I receive from my internet supplier is the network name and the wep secure code. I really appreciate it.

---

### Post by bkratz on 2009-12-31
> **PECHAS said:**
> Hello,

I would like to receive some help to set up a wireless connection on Ubuntu, what I receive from my internet supplier is the network name and the wep secure code. I really appreciate it.



Well you really need to give a little more detail. It depends on what wireless card you have (pci or usb) and what type it is. Go to 
Applications>>Accessories>>terminal and type in

lspci -nn   (that is LSPCI in lowercase) and also lsusb and copy and paste the outputs here so someone can see what your wireless card is or you can probably just decode it and report back and tell us. We then have a starting point.

---

### Post by PECHAS on 2010-01-01
> **bkratz said:**
> Well you really need to give a little more detail. It depends on what wireless card you have (pci or usb) and what type it is. Go to 
Applications>>Accessories>>terminal and type in

lspci -nn   (that is LSPCI in lowercase) and also lsusb and copy and paste the outputs here so someone can see what your wireless card is or you can probably just decode it and report back and tell us. We then have a starting point.
Hello,

Here is the data from those instructions, thank you once again.

00:00.0 Host bridge [0600]: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub [8086:7124] (rev 03)
00:01.0 VGA compatible controller [0300]: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller [8086:7125] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801AA PCI Bridge [8086:2418] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801AA ISA Bridge (LPC) [8086:2410] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801AA IDE Controller [8086:2411] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801AA USB Controller [8086:2412] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801AA AC'97 Audio Controller [8086:2415] (rev 02)
01:0a.0 Communication controller [0780]: Agere Systems LT WinModem [11c1:044e] (rev 02)
01:0d.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)


 lsusb
Bus 001 Device 004: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 003: ID 0424:0140 Standard Microsystems Corp. 
Bus 001 Device 002: ID 1737:0071  
Bus 001 Device 001: ID 0000:0000

---

