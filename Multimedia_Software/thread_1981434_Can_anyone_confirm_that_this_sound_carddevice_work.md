---
title: "Can anyone confirm that this sound card/device works in 12.04?"
date: 2012-05-16
forum: Multimedia Software
---

### Post by MakOwner on 2012-05-16
It's a Diamond Sound Tube USB sound card model XSTU21.

I tried an ASUS card I saw mentioned on the forums, and it doesn't work, and getting ASUS support on the line is like a self-administering an  appendectomy.


This ASUS Xonar DX (PCIe Sound Card) does NOT work.

```

02:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
	Subsystem: ASUSTeK Computer Inc. Virtuoso 100 (Xonar DX)
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 6000ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: I/O ports at ec00 [size=256]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: snd_virtuoso
	Kernel modules: snd-virtuoso

```

---

