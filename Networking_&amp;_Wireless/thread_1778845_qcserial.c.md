---
title: "qcserial.c"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by Cpstans on 2011-06-09
Hi,
First hello I am super new to Linux and super super new to problems that I am unable to solve.

I have a Compaq Mini 100c 1110SA which was supplied with Windows XP however, due to a number of problems I decided to use a nice 'simple' system and was recommended Ubuntu.

So far I am 100% happy with its design, the software and the GUI however after a week of searching, typing stuff into terminal with no idea what it does and then downloading random packages I am no nearer to sorting my issue.

I have a HP Gobi 3g modem which is not recognized on my system. I have tried all sorts but it keeps coming back to qcserial is not in porc/modules?

Here is some information which seems to be required when posting...

lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1fea:0008  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
02:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)

I have tried follow the instructions here : [http://ubuntuforums.org/archive/index.php/t-1593581.html](http://ubuntuforums.org/archive/index.php/t-1593581.html) However at  sudo rmmod qcserial i recieve ERROR: Module qcserial does not exist in /proc/modules

I have searched for this file and it does not seem to be anywhere.
Can someone advise me as to what I need to do?

Even if the answer is 'it will not work under 2.6.38.8'

Thank you in advance

---

