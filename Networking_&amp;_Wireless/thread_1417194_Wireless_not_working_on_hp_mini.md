---
title: "Wireless not working on hp mini"
date: 2010-02-27
forum: Networking &amp; Wireless
---

### Post by bkrober@swbell.net on 2010-02-27
I loaded Ubuntu on my mini and everything worked fine except it didn't recognize my wireless card in my HP 210 mini. Anyone have any suggestions.

---

### Post by bkratz on 2010-02-27
> **bkrober@swbell.net said:**
> I loaded Ubuntu on my mini and everything worked fine except it didn't recognize my wireless card in my HP 210 mini. Anyone have any suggestions.



First thing we would need to do is determine what wireless card you have. Go to Applications>>Accessories>>Terminal and enter:

lspci | grep Wireless

(that is LSPCI in lowercase and W in upper), if you don't get a response then try 

lspci -nn

Which would give all the pci hardware, and you would have to find the wireless description yourself.
When you do find  the correct information, copy/paste it back here, so someone can determine the correct direction to follow.

---

### Post by gcaw on 2010-11-03
Here's what I get as output, with the same problem:

[INDENT]00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GME Express Memory Controller Hub [8086:27ac] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GME Express Integrated Graphics Controller [8086:27ae] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
[B]01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
[/B]02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]
[/INDENT]

Any thoughts?

Many thanks

---

