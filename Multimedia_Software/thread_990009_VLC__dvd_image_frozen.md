---
title: "VLC : dvd image frozen"
date: 2008-11-22
forum: Multimedia Software
---

### Post by siilexx on 2008-11-22
Hi,

I'm trying to play dvd with VLC in xubuntu 8.10 and I have the following problem:

The dvd start correctly, opening the menu with sound and image. Then when I start the movie, the video stays stucked on the first image of the film. Actually the time counter is progressing but not the video on the screen, and I also hear like one second of sound. 

Could you help me please ?
I'm also trying to make my real magic hollywood+ card working but without success until now.
I've already installed a lot of packages (libdvd, dxr3,...) but something should be wrong somehere...

Thank you.


output of lspci -vv :

01:00.0 VGA compatible controller: NVidia / SGS Thomson (Joint Venture) Riva128 (rev 22)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e6000000 (32-bit, prefetchable) [size=16M]
	[virtual] Expansion ROM at e5000000 [disabled] [size=4M]
	Capabilities: <access denied>
	Kernel modules: rivafb



00:0b.0 Multimedia controller: Sigma Designs, Inc. REALmagic Hollywood Plus DVD Decoder (rev 02)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at e8000000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>


Same output with sudo:
01:00.0 VGA compatible controller: NVidia / SGS Thomson (Joint Venture) Riva128 (rev 22)
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (750ns min, 250ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at e4000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at e6000000 (32-bit, prefetchable) [size=16M]
	[virtual] Expansion ROM at e5000000 [disabled] [size=4M]
	Capabilities: [44] AGP version 1.0
		Status: RQ=5 Iso- ArqSz=0 Cal=0 SBA- ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
	Kernel modules: rivafb



00:0b.0 Multimedia controller: Sigma Designs, Inc. REALmagic Hollywood Plus DVD Decoder (rev 02)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64
	Interrupt: pin A routed to IRQ 5
	Region 0: Memory at e8000000 (32-bit, non-prefetchable) [size=1M]
	Capabilities: [40] Power Management version 1
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

---

### Post by Izek on 2008-11-22
If the bar progresses, but no image or sound is progressing (or vice versa) then it usually has to do with the codec interfacing with the player/system. Have you tried to see if Totem will play the DVD?

---

