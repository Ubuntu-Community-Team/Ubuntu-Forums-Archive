---
title: "[SOLVED] projecting with linux"
date: 2007-06-20
forum: Multimedia &amp; Video
---

### Post by boldexplorer on 2007-06-20
I have an Acer TravelMate 260 that I used to be able to hook up to almost any Data Projector and display my data. 
Since installing Ubuntu I have not been able to do this.
Is it possible to do? Is there something that I need to set up? 
my lspci looks like this: 

00:00.0 Host bridge: Intel Corporation 82830 830 Chipset Host Bridge (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)
00:02.1 Display controller: Intel Corporation 82830 CGC [Chipset Graphics Controller]
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #1) (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB (Hub #2) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:09.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller

Thanks

---

### Post by boldexplorer on 2007-06-21
have sorted out the problem.
Was a VGA output.  Simply restart X server.
 
See [http://ubuntuforums.org/showthread.php?p=2887420#post2887420](http://ubuntuforums.org/showthread.php?p=2887420#post2887420) for more info!

---

