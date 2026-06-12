---
title: "Compro T100 tuner"
date: 2010-01-29
forum: Multimedia Software
---

### Post by rbradley on 2010-01-29
Hi,
I'm trying to get a Compro T100 tuner working with MythTv, but it shows up as a T750

>lspci gives:

Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
	Subsystem: Compro Technology, Inc. Device [185b:c900]
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (21000ns min, 8000ns max)
	Interrupt: pin A routed to IRQ 16
	Region 0: Memory at e2000000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=1 PME-
	Kernel driver in use:  
	Kernel modules: saa7134

>dmesg gives:

[ 9.113841] saa7130/34: v4l2 driver version 0.2.15 loaded
[    9.113925] saa7134 0000:00:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.113934] saa7133[0]: found at 0000:00:05.0, rev: 209, irq: 16, latency: 32, mmio: 0xe2000000
[    9.113943] saa7133[0]: subsystem: 185b:c900, board: Compro VideoMate T750 [card=139,autodetected]
[    9.113972] saa7133[0]: board init: gpio is 843f00
[    9.113982] IRQ 16/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.264011] saa7133[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    9.264024] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[    9.264034] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 87 ff ff ff ff
[    9.264044] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264054] saa7133[0]: i2c eeprom 40: ff d5 00 c4 86 1e ff ff ff ff ff ff c6 ff 07 ff
[    9.264063] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[    9.264073] saa7133[0]: i2c eeprom 60: 30 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264082] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264092] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264102] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264111] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264121] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264130] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264140] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264149] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264159] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

I've loaded xc3028-v27.fw but the card isn't recognized.

Anyone out there got any ideas?

Thanks in advance.
Ross.

---

### Post by sports.car.guy on 2010-01-29
> **rbradley said:**
> Hi,
I'm trying to get a Compro T100 tuner working with MythTv, but it shows up as a T750

>lspci gives:

Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
    Subsystem: Compro Technology, Inc. Device [185b:c900]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32 (21000ns min, 8000ns max)
    Interrupt: pin A routed to IRQ 16
    Region 0: Memory at e2000000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 PME-Enable- DSel=0 DScale=1 PME-
    Kernel driver in use:  
    Kernel modules: saa7134

>dmesg gives:

[ 9.113841] saa7130/34: v4l2 driver version 0.2.15 loaded
[    9.113925] saa7134 0000:00:05.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.113934] saa7133[0]: found at 0000:00:05.0, rev: 209, irq: 16, latency: 32, mmio: 0xe2000000
[    9.113943] saa7133[0]: subsystem: 185b:c900, board: Compro VideoMate T750 [card=139,autodetected]
[    9.113972] saa7133[0]: board init: gpio is 843f00
[    9.113982] IRQ 16/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[    9.264011] saa7133[0]: i2c eeprom 00: 5b 18 00 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[    9.264024] saa7133[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[    9.264034] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 87 ff ff ff ff
[    9.264044] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264054] saa7133[0]: i2c eeprom 40: ff d5 00 c4 86 1e ff ff ff ff ff ff c6 ff 07 ff
[    9.264063] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[    9.264073] saa7133[0]: i2c eeprom 60: 30 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264082] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264092] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264102] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264111] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264121] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264130] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264140] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264149] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[    9.264159] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff

I've loaded xc3028-v27.fw but the card isn't recognized.

Anyone out there got any ideas?

Thanks in advance.
Ross.

That is the card being recognized from what it looks like. Otherwise it would not be giving the tuner chip information like it is. Under Linux a piece of hardware that shares the capabilities with others can get labelled by a generic name for the hardware family it is from.

---

### Post by rbradley on 2010-01-29
Hi,
Thanks for the reply.  The problem is that the T750 appears to have no supporting drivers and I was hoping that someone could tell me:

-  How to make it look like a T100 card and where to get the appropriate drivers

or, failing that,

-  How to make it look like a Compro card that does have drivers available.

Regards,
Ross

---

