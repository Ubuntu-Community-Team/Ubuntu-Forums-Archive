---
title: "sound out of case speaker?!?"
date: 2008-09-11
forum: Multimedia Software
---

### Post by anystupidname on 2008-09-11
So I just installed a new Kubuntu 8.04 on a Dell Gx620 and sound is weak and coming out of only the right speaker in my headphones and out of the case speaker?!? I had Debian 4.1 on there before and the same setup and sound was fine. Any suggestion would be appreciated.

---

### Post by anystupidname on 2008-10-30
anybody?!? I just installed Ubuntu 8.10 and it exhibits the same behaviour. Sound come out of the case speaker and not the speakers plugged into the sound jacks. WTF?!?

This is lspci -vvv output

```
00:1e.2 Multimedia audio controller: Intel Corporation 82801G (ICH7 Family) AC'97 Audio Controller (rev 01)
	Subsystem: Dell Device 01ad
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 0
	Interrupt: pin A routed to IRQ 23
	Region 0: I/O ports at ec00 [size=256]
	Region 1: I/O ports at e8c0 [size=64]
	Region 2: Memory at febffa00 (32-bit, non-prefetchable) [size=512]
	Region 3: Memory at febff900 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

```

---

