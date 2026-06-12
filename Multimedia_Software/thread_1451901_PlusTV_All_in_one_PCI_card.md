---
title: "PlusTV All in one PCI card"
date: 2010-04-11
forum: Multimedia Software
---

### Post by blueskies1977 on 2010-04-11
[LEFT]I have a KWorld PlusTV all in one card (model pl610) which uses the Phillips 713x series of chipsets.

This is the lspci output for the card:
 
```
06:08.0 0480: 1131:7133 (rev d1)
    Subsystem: 17de:7256
    Flags: bus master, medium devsel, latency 32, IRQ 23
    Memory at f9fff800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: saa7134
    Kernel modules: saa7134

```has anyone had any success in finding the relevant modprobe details to enable this card to work?
[/LEFT]

---

### Post by cogvos on 2010-09-04
I also have this card and I am also stuck :(

lspci -vv gives

03:08.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
	Subsystem: KWorld Computer Co. Ltd. Device 7256
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (21000ns min, 8000ns max)
	Interrupt: pin A routed to IRQ 20
	Region 0: Memory at fddff000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

This beast also has a firewire input wich I think is reported thus:-

03:09.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link) (prog-if 10)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 64 (500ns min, 1000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 21
	Region 0: Memory at fddfe000 (32-bit, non-prefetchable) [size=2K]
	Region 1: Memory at fddf8000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: ohci1394
	Kernel modules: firewire-ohci, ohci1394

There is a thread here - [http://ubuntuforums.org/showthread.php?t=884438&highlight=Kworld](http://ubuntuforums.org/showthread.php?t=884438&highlight=Kworld) - which shows how to get the SAA7134 chipset working. Sadly I really don't understand it and so cannot see if I can modify it for the SAA7131/SAA7133/SAA7135. 

dmesg | grep saa gives 

[   30.233508] saa7130/34: v4l2 driver version 0.2.15 loaded
[   30.233575] saa7134 0000:03:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   30.233585] saa7133[0]: found at 0000:03:08.0, rev: 209, irq: 20, latency: 64, mmio: 0xfddff000
[   30.233595] saa7133[0]: subsystem: 17de:7256, board: UNKNOWN/GENERIC [card=0,autodetected]
[   30.233611] saa7133[0]: board init: gpio is 100
[   30.233620] IRQ 20/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   30.388018] saa7133[0]: i2c eeprom 00: de 17 56 72 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   30.388029] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff 01
[   30.388038] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 00 fe ff ff ff ff
[   30.388047] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.388055] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 56 ff ff ff ff ff ff
[   30.388064] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.388072] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.388081] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.388090] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.388098] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.388107] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.388115] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.388124] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.388132] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.388141] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.388149] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   30.389118] saa7133[0]: registered device video0 [v4l2]
[   30.389141] saa7133[0]: registered device vbi0
[   30.403431] saa7134 ALSA driver for DMA sound loaded
[   30.403445] IRQ 20/saa7133[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   30.403465] saa7133[0]/alsa: saa7133[0] at 0xfddff000 irq 20 registered as card -2

I think that this means that the board has been detected - so you don't need to modprob? But am not sure about the fact that one part is saying it is generic. It could be due to the fact that this card has an analogue and digital receiver built in as well as composite and the firewire(?)

All I know is that mythtv is living up to its name and refusing to display anything.

Can anyone help here? What - if anything - do I need to modify do from the thread I have highlighted to get the card to work. In particular as they are shutting down analogue tv here in the UK soon - what do I need to do to get the DVB (digital) tuner to work on Ubuntu 9.10? 

[As an aside I also have 10.whatever but hate the startup screen .... so am sticking to 9.10 for now it just looks so much more professional.]

---

