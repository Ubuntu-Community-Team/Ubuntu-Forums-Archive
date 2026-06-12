---
title: "No sound jaunty..."
date: 2009-04-30
forum: Multimedia Software
---

### Post by Aesculaius on 2009-04-30
Is it me..? Or is Jaunty really buggy..? Im having so many problems with it.. 3 finger linux shuffle doesnt work.. I spent over a day getting my network to run.. and now my sound doesnt work! The sound worked originally when I first installed Janunty. Between then and now I did alot of stuff.. I installed a bunch of packages.. Wine.. many lib-devel packages for wine, and updates. now my sound doesnt work.. heres my printout of xorg.config and lspci -vv:

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
	Subsystem: ABIT Computer Corp. Device 100a
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin B routed to IRQ 17
	Region 0: I/O ports at d800 [size=256]
	Region 1: I/O ports at dc00 [size=64]
	Region 2: Memory at fd001000 (32-bit, non-prefetchable) [size=512]
	Region 3: Memory at fd002000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0



Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

---

### Post by saitan on 2009-05-03
[This article]("http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html") helped me:

---

