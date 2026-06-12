---
title: "Problems with video capture"
date: 2009-01-14
forum: Multimedia Software
---

### Post by tanis143 on 2009-01-14
Ok, I'm still a greenhorn to linux. I've just made the fulltime switch about a week ago. For the most part, got everything working (haven't tried burning a disk yet, but I've found ton of programs to do that). What I've not got working yet is my video capture card. Its a V-Stream Xpert 2000Pro video capture card, not a tv tuner card. Using XawTV I get video, but no audio. My capture card uses a dongle to receive audio and video input, then has an audio line going to the line in on my sound card. I took the audio out from the dongle and hooked it directly to a set of speakers and still got no audio. I know the card works because it worked fine in XP last week before I switched. I'm using Ubuntu 8.1. Not sure what info I need to give for help.

edit: 

Here is the lspci for the card:

01:07.0 Multimedia video controller: Conexant Systems, Inc. CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (5000ns min, 13750ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 17
	Region 0: Memory at f6000000 (32-bit, non-prefetchable) [size=16M]
	Capabilities: [44] Vital Product Data <?>
	Capabilities: [4c] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: cx8800
	Kernel modules: cx8800

---

### Post by tanis143 on 2009-01-15
So no help on this? I've scoured the net and how to's, I have found others with this problem, and so far no real help on how to fix this issue. I've now tried another program, TVTime and same issue, no audio at all.

---

