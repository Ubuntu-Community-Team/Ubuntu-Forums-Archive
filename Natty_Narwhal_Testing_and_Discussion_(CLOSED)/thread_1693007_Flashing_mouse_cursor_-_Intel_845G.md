---
title: "Flashing mouse cursor - Intel 845G"
date: 2011-02-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Amos91 on 2011-02-22
Hello,

Currently been using the latest alpha 2 on my ancient Samsung V25 laptop.  This release, using the "nomodeset" command in grub has stopped blank screen issues that had plagued me in previous releases.

However, another issue has been created.  Basically, hovering over selections in menus, or over hyperlinks in firefox or chrome, and whilst scrolling webpages, the mouse cursor will disappear.  As soon as I move the mouse it instantly reappears and works fine until I do something like I mentioned above.  This has not happened before on Ubuntu 9.04/10, 10.10 and Linux Mint 9.

I believe it has something to do with compiz or unity but any suggestions are welcome as to how to fix this.

My Lspci:

```
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 02)
02:03.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 80)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 82)
02:0d.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 Network controller: RaLink RT2500 802.11g (rev 01)
```

Thanks, 
Amos

---

