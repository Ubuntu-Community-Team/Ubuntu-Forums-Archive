---
title: "Wireless not working Acer Aspire One"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by Mercutio879 on 2009-02-08
Picked up an Acer Aspire One 110, and have Ubuntu 8.10 installed. According to every post I've read, after the initial install, I should see Atheros drivers in the Hardware drivers. I see nothing. Also, most also say that I should have an Atheros AR242x chip inside my little laptop. The sticker on the bottom says: Atheros AR5BXB63. I can't get the wireless to work at all. I've googled for the chip as stated on the bottom, and those instructions don't work. I've tried the instructions that are in the Aspire 110L guide, and with both the ath5k and the madwifi, I get nothing. Any help is appreciated.

lspci gives me this:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
03:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
03:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
03:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

---

