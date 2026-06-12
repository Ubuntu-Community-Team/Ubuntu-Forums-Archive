---
title: "Best supported PCIe sound card?"
date: 2012-05-06
forum: Multimedia Software
---

### Post by MakOwner on 2012-05-06
Trying this again.

I'm looking for a supported sound card that will work out-of-the-box with a server install of Ubuntu.  I found an ASUS card that works, but requires a desktop install and configuration with GUI tools.
I'm replacing an older server with PCI only I/O slots and currently using this card. This card just *works* with a 10.04 LTS install.

```

00:0e.0 Multimedia audio controller: Ensoniq 5880B [AudioPCI] (rev 02)
	Subsystem: Ensoniq Device 2000
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=slow >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (3000ns min, 32000ns max)
	Interrupt: pin A routed to IRQ 7
	Region 0: I/O ports at ed80 [size=64]
	Capabilities: [dc] Power Management version 1
		Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Kernel driver in use: ENS1371
	Kernel modules: snd-ens1371

```


I'm looking for a replacement sound card for a new server with only PCIe and PCIX I/O slots that works as is, or can be configured with command line only tools.

---

