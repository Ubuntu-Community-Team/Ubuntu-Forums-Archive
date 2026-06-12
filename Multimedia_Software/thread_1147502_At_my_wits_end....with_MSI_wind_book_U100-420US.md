---
title: "At my wits end....with MSI wind book U100-420US"
date: 2009-05-03
forum: Multimedia Software
---

### Post by robfindlay on 2009-05-03
Out of the box in XP, the video was fantastic, no problem playing xvids etc.

the netbook remix has been a nightmare.. compiz will not load, graphics are twitchy, i can no longer playback ANY video. 

Here are my specs: 

lspcis -vv:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at dfe80000 (32-bit, non-prefetchable) [size=512K]
	Region 1: I/O ports at d100 [size=8]
	Region 2: Memory at c0000000 (32-bit, prefetchable) [size=256M]
	Region 3: Memory at dff00000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Micro-Star International Co., Ltd. Device 0110
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Region 0: Memory at dfe00000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

```

And my xorg: 
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2304 1024
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```

I REALLY don't want to go back to windows if i cant get this to work.

-Rob

---

### Post by robfindlay on 2009-05-03
K.....partly my fault...I had a dual screen setup and virtual screen size was killing everything. 

Any thoughts looking at the above on how to make this work on dual screen? 


Rob

---

