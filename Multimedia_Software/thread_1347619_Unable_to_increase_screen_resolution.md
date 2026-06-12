---
title: "Unable to increase screen resolution"
date: 2009-12-06
forum: Multimedia Software
---

### Post by maheshnew on 2009-12-06
Hi,
I am new user of Linux and have installed Ubuntu recently.

I am not able get screen resolution more than 800*600, whereas when i was using windows, my screen was set at 1024*768.

In the display configuration I can see only 2 resolutions and its not detecting my LCD as well. I have a LG 17 inches LCD 566LE. Below is the dump of command lspci. Can someone help me setting the display right.

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:01.0 Ethernet controller: Winbond Electronics Corp W89C940
01:02.0 Ethernet controller: MYSON Technology Inc SURECOM EP-320X-S 100/10M Ethernet PCI Adapter

Thanks
Mahesh

---

### Post by natex on 2009-12-06
Hi. I found this on another forum and looks like it may help you. Basically it boils down to adding the correct lines to your /etc/X11/xorg.conf file.

[http://www.linuxquestions.org/questions/ubuntu-63/intel-82845g-graphics-controller-352262/](http://www.linuxquestions.org/questions/ubuntu-63/intel-82845g-graphics-controller-352262/)

Let me know if you need more help after reviewing the link!

natex

---

