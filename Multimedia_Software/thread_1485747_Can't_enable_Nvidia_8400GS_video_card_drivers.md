---
title: "Can't enable Nvidia 8400GS video card drivers"
date: 2010-05-17
forum: Multimedia Software
---

### Post by ronnielsen1 on 2010-05-17
I've tried to enable the drivers for a Nvidia 8400GS video card on Ubuntu 10.04. I've tried change desktop background > visual effects. It tells me Desktop effects can't be enabled. Sudo jockey-gtk looks and tells me no proprietary drivers are in use by my system. I've tried installing from Nvidia's site and that seems to go okay but doesn't seem to work. I have an internal video card that can't be turned off in BIOS )either ON or AUTO) that might be causing me problems.
Lspci:
> ron@desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:04.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
01:05.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
ron@desktop:~$ 


---

### Post by ronnielsen1 on 2010-05-18
I guess I have to go back to an earlier version of ubuntu? If that's the case with a 512M video card, there's going to be a lot of computers that won't be able to run Ubuntu 10.04

---

