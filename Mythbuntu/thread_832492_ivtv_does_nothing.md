---
title: "ivtv does nothing"
date: 2008-06-17
forum: Mythbuntu
---

### Post by mat1t on 2008-06-17
Complete beginner at this, have tried following some instructions but appear to have got lost. The cards have worked under Myth before, and it's working under windows as well (dual boot) but am looking at making the transition! :)

I've obtained the firmware from hauppauge's site for the PVR-500, and copied it to the /lib/firmware/2.6.24-19-generic/ folder as described [here]("http://ivtvdriver.org/index.php/Firmware").

after a restart and running "modprobe ivtv" the only output of ivtv is below:
```
dmesg | grep ivtv
[  121.186368] ivtv:  Start initialization, version 1.1.0
[  121.186429] ivtv:  End initialization

```

I'm a bit stuck as to where to go from here, so I've included some output below:

```
lspci
00:00.0 Host bridge: Intel Corporation 82875P/E7210 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82875P Processor to AGP Controller (rev 02)
00:06.0 System peripheral: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:00.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
02:02.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:02.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
02:02.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
02:03.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:0c.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

```

```
lsusb
Bus 008 Device 002: ID 2040:9951 Hauppauge
Bus 008 Device 001: ID 0000:0000
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 002: ID 050d:0013 Belkin Components
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 0609:031d SMK Manufacturing, Inc.
Bus 001 Device 001: ID 0000:0000
```

If you need any more details then please don't hesitate to ask. I'm stumped.

---

