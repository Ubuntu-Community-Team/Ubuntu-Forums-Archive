---
title: "Atheros AR5001X Wireless Not Working"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by Rfgordils on 2009-10-26
Hi, I don't know very much about wireless cards in Ubuntu. I've been trying to get my Atheros AR5001X card running, but nothing seems to work.

I'm running a fresh install of Ubuntu 9.04 on a Dell Dimension B110.

When I type lspci in the terminal, my output is:

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 Non-VGA unclassified device: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
01:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
---------------------------------------------------------------------

I've tried downloading the driver for it and installing it with ndiswrapper, but it hasn't worked. I'm not really sure what I'm doing with it, but I've tried three different drivers that I found online after googling "Atheros AR5001X driver". The three drivers show up in ndiswrapper as: net5211, netathw and netathwx. 

My wired connection is working perfectly, wireless is the only thing not working. Oh, and it has worked in the past with Windows, and it previously worked on an older install of Ubuntu 8.04 where it was automatically taken care for me. So the hardware definitely works.

,Thanks

---

### Post by Fire_Chief on 2009-11-05
Normally, this would be fixed by installing the Madwifi package from the repos. The Madwifi package heavily depends on the HAL framework for its hardware detection and as of 9.10 HAL is being depreciated in favor of Udev. So, naturally they cannot include the madwifi package in 9.10 and continue moving forward with removing HAL.

The newer ath5k package does not support your older wireless chipset.

I did find this forum thread ([http://ubuntuforums.org/showthread.php?t=1309072]("http://ubuntuforums.org/showthread.php?t=1309072")) which offers directions on installing the current madwifi driver and getting the card working. I've not tested the procedure but it may work for you.

Cheers!

---

