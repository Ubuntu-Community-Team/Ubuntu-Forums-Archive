---
title: "Intel 82801G no headphone sound"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by Centaur5 on 2006-06-15
I have Dapper Drake installed with the newest updates.  My sound works fine through the speakers on my laptop but I would really like to get the headphone jack working for trips when I need them.  It's a Sony Vaio VGN-SZ140P and has an Intel HDA 82801G Sound Card.  Here are the results from lspci:

0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Graphics Port (rev 03)
0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
0000:00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
0000:00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
0000:00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
0000:00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
0000:00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
0000:00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
0000:00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
0000:00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
0000:00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
0000:00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
0000:00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
0000:00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controllers cc=IDE (rev 02)
0000:00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 01d8 (rev a1)
0000:06:00.0 Network controller: Intel Corporation: Unknown device 4222 (rev 02)0000:07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 Fast Ethernet Controller (rev 15)
0000:09:04.0 CardBus bridge: Texas Instruments: Unknown device 8039
0000:09:04.1 FireWire (IEEE 1394): Texas Instruments: Unknown device 803a
0000:09:04.2 Mass storage controller: Texas Instruments: Unknown device 803b

---

### Post by Centaur5 on 2006-06-27
Just a note for anybody with this sound card I was able to fix the problem by upgrading to the 2.6.17 kernel using this [howto]("http://www.ubuntuforums.org/showthread.php?t=157560&highlight=kernel+2.6.17").    The new kernel added lots of new support for this sound card but if you don't want to risk compiling an unsupported kernel you might want to wait til the features are put into Dapper.

---

