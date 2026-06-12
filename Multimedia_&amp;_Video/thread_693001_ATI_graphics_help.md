---
title: "ATI graphics help"
date: 2008-02-10
forum: Multimedia &amp; Video
---

### Post by ser_enity on 2008-02-10
Can anyone help me with this issue that I'm having with my graphics card?

When I try to load a game, this is what I get returned:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
ERROR: "The required OpenGL extension '&#65533;s' is not supported by your current driver version or graphics card." at graphics/gropenglextension.cpp:394

Anyone know what this means or how to fix it? :confused: I have an ATI graphics card, which I've had some issues with before in linux.

Thanks to anyone who posts!

---

### Post by polmir on 2008-02-10
Type in terminal
```
lspci -vv | grep VGA
```
 post output of it

---

### Post by ser_enity on 2008-02-10
Here's what I got:
```

Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
BridgeCtl: Parity- SERR- NoISA+ VGA- MAbort- >Reset- FastB2B-
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
BridgeCtl: Parity- SERR+ NoISA- VGA- MAbort- >Reset- FastB2B-
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M] (prog-if 00 [VGA])
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
 BridgeCtl: Parity- SERR- ISA- VGA- MAbort- >Reset+ 16bInt+ PostWrite+
Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-

```
Thanks

---

### Post by polmir on 2008-02-11
Please read this:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-d8c6fd05bce340dfc3ad483abf0e18997868540b")
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")
[http://m3n3chm0.wordpress.com/2007/05/01/ati-radeon-xpress-200m-ubuntu/]("http://m3n3chm0.wordpress.com/2007/05/01/ati-radeon-xpress-200m-ubuntu/")

---

