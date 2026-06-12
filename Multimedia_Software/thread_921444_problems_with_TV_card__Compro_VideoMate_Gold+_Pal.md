---
title: "problems with TV card : Compro VideoMate Gold+ Pal"
date: 2008-09-16
forum: Multimedia Software
---

### Post by Maxssss on 2008-09-16
hello Everybody,

I've been trying to make Analog TV work on my Ubuntu 8.04 (Media Centre) but i really cant get it to work.

it just isnt able to find any channels, in any program i use.

i have been reading a whole lot on ubuntu forums but none of the info is actually for my card.
ive also tryed the mythbuntu forums but still no luck.

i am using an Compro VideoMate Gold+ Pal card, anybody any suggestion or ideas where to look for some how to?


Greetzz Maxs


below ill post some card info.

sudo lspci -s 02:00 -v

02:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
	Subsystem: Compro Technology, Inc. Compro VideoMate Gold+ Pal
	Flags: bus master, medium devsel, latency 32, IRQ 21
	Memory at feaffc00 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [40] Power Management version 1

dmesg

[   38.642374] saa7134[0]: found at 0000:02:00.0, rev: 1, irq: 21, latency: 32, mmio: 0xfeaffc00
[   38.642383] saa7134[0]: subsystem: 185b:c200, board: Compro VideoMate Gold+ Pal [card=49,autodetected]
[   38.642402] saa7134[0]: board init: gpio is cc000e
[   38.642516] input: saa7134 IR (Compro VideoMate Go as /devices/pci0000:00/0000:00:1e.0/0000:02:00.0/input/input4
[   38.860989] saa7134[0]: i2c eeprom 00: 5b 18 00 c2 ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861007] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861022] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861037] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861051] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861065] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff 01 01 ff 01 ff 00 07 34 23 cb
[   38.861079] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861094] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861108] saa7134[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861122] saa7134[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861137] saa7134[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861151] saa7134[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861166] saa7134[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861180] saa7134[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861195] saa7134[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   38.861209] saa7134[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   39.132395] parport_pc 00:09: reported by Plug and Play ACPI
[   39.132425] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   39.156764] tuner' 0-0060: chip found @ 0xc0 (saa7134[0])
[   39.156828] tea5767 0-0060: type set to Philips TEA5767HN FM Radio
[   39.172623] tuner' 0-0063: chip found @ 0xc6 (saa7134[0])
[   39.180633] tuner' 0-0068: chip found @ 0xd0 (saa7134[0])
[   39.280624] tuner-simple 0-0063: creating new instance
[   39.280631] tuner-simple 0-0063: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[   39.302988] saa7134[0]: registered device video0 [v4l2]
[   39.303020] saa7134[0]: registered device vbi0
[   39.303049] saa7134[0]: registered device radio0
[   39.512704] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16

---

