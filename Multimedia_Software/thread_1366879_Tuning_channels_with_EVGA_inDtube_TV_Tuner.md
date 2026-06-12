---
title: "Tuning channels with EVGA inDtube TV Tuner"
date: 2009-12-28
forum: Multimedia Software
---

### Post by linuxuser21 on 2009-12-28
I just got the EVGA inDtube Digital TV tuner and I cannot seem to get any channels.  It works with the S-Video and composite inputs but I can't pick up any channels.  I am working with TVtime.

---

### Post by HappyFeet on 2009-12-28
Post the output of
```
lspci
```

---

### Post by linuxuser21 on 2009-12-28
```
lspci:
00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:08.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)
```

---

### Post by HappyFeet on 2009-12-29
Is the tv tuner usb? If so, post the output of
```
lsusb
```

---

### Post by linuxuser21 on 2009-12-29
Yes, it's a USB
```
lsusb:
Bus 001 Device 005: ID eb1a:2883 eMPIA Technology, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 002: ID 03f0:7304 Hewlett-Packard DeskJet 35xx
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by HappyFeet on 2009-12-29
Unfortunately, there is no info I can use to determine the chipset of the tuner. Hopefully someone else will be able to help.

---

### Post by linuxuser21 on 2009-12-29
Thank you for trying.  This particular device is proving to be quite hard to find info on.

---

### Post by linuxuser21 on 2009-12-30
Bump

---

### Post by linuxuser21 on 2010-01-03
Still bumping

---

### Post by linuxuser21 on 2010-01-05
Does anyone know if this tuner is even able to pick up modern-day (United States) signals?

---

### Post by drdanielfc on 2010-08-01
Hello, I'm having the same problem with the exact same tuner. I figured I'd revive this thread instead of creating a new one. Is there anyone out there that could help? I've already attempted to use the tuner through wine but it didnt detect the tuner at all.

Thanks ahead of time,
Daniel

---

### Post by tjjani on 2011-06-12
Here is what I did to fix the mysterious "no chanels" problem with the EVGA Indtube that I had been working on for several months and unhappily dual booting into windows to use it:
You need to load the firmware for the chipset xc3082L according to this page: [http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028](http://www.linuxtv.org/wiki/index.php/Xceive_XC3028/XC2028)
(Be sure to download the firmware for the xc3028L and not the xc3028. Then copy it to your /lib/firmware/ folder.

All over these wikis and the interwebs it talks about the em28xx and this card. Once you find out that you also need the firmware for the XC3082L also, you will find the ATSC channels in the usual way as everyone else.

---

