---
title: "Asus WL-138g not recognized?"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by c-shadow on 2009-12-07
My card is not supported by native driver, after some googleing around I found it's supposed to work with ndiswrapper. Tried with ndisgtk, driver installs, but it says "Hardware present: No".
Tried also installing from terminal but no luck:
```

sudo ndiswrapper -i mrv8ka51.inf
installing mrv8ka51 ...

ndiswrapper -l
mrv8ka51 : driver installed

```

But no "device present" :sad:

```
uname -a
Linux Amber 2.6.27-14-generic #1 SMP Mon Aug 31 13:01:41 UTC 2009 i686 GNU/Linux

```

```
 ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.27-14-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.53
vermagic:       2.6.27-14-generic SMP mod_unload modversions 586

```

```

lspci -nn
03:05.0 Non-VGA unclassified device [0000]: Gammagraphx, Inc. Device [0000:82b0]

```

```

lspci -vvv
03:05.0 Non-VGA unclassified device: Gammagraphx, Inc. Device 82b0
	Subsystem: Genoa Systems Corp Device 138f
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF+ FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
	Latency: 0, Cache Line Size: 16 bytes
	Interrupt: pin A routed to IRQ 4
	Region 1: Memory at <unassigned> (64-bit, non-prefetchable) [disabled]
	Region 3: Memory at <unassigned> (64-bit, non-prefetchable) [disabled]
	Region 5: Memory at <invalid-64bit-slot> (64-bit, non-prefetchable) [disabled]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [44] Slot ID: 0 slots, First-, chassis 00

```

Something is strange with this card, unclassified device?
gnome-device-manager sees the card, but it seems it's missing the id?
Tried with unbuntu 8.10, 9.04 and 9.10, but no luck.
Any help with this card?
lspci in 9.04 says this:
```

03:05.0 Non-VGA unclassified device: Gammagraphx, Inc. (or missing ID) Device 82b0
	Subsystem: Genoa Systems Corp Device 138f
	Control: I/O- Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR+ INTx-
	Latency: 0, Cache Line Size: 16 bytes
	Interrupt: pin A routed to IRQ 4
	Region 0: Memory at <ignored> (32-bit, non-prefetchable) [disabled]
	Region 1: Memory at <unassigned> (64-bit, non-prefetchable) [disabled]
	Region 3: Memory at <unassigned> (64-bit, non-prefetchable) [disabled]
	Region 5: Memory at <invalid-64bit-slot> (64-bit, non-prefetchable) [disabled]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>

```

---

