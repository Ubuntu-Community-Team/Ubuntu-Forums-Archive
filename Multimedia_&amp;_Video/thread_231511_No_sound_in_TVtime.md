---
title: "No sound in TVtime"
date: 2006-08-07
forum: Multimedia &amp; Video
---

### Post by Jaxilian on 2006-08-07
I am using ubuntu 6.06.
I get this from dmesg:

[17179591.380000] ACPI: PCI Interrupt 0000:02:03.0[A] -> GSI 23 (level, low) -> IRQ 209
[17179591.380000] saa7133[0]: found at 0000:02:03.0, rev: 240, irq: 209, latency: 128, mmio: 0xb0000800
[17179591.380000] saa7133[0]: subsystem: 14c0:1212, board: LifeView FlyTV Platinum Mini2 [card=74,autodetected]
[17179591.380000] saa7133[0]: board init: gpio is 10400
[17179591.380000] input: saa7134 IR (LifeView FlyTV Plat as /class/input/input5


[17179591.560000] saa7133[0]: i2c eeprom 00: c0 14 12 12 10 28 ff ff ff ff ff ff ff ff ff ff
[17179591.560000] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179591.560000] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179591.560000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179591.560000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179591.560000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179591.560000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179591.560000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179591.696000] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[17179591.720000] cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x370-0x377
[17179591.724000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179591.724000] cs: IO port probe 0x820-0x8ff: clean.
[17179591.724000] cs: IO port probe 0xc00-0xcf7: clean.
[17179591.724000] cs: IO port probe 0xa00-0xaff: clean.
[17179591.744000] tuner 0-004b: setting tuner address to 61
[17179591.784000] tuner 0-004b: tuner: type set to tda8290+75


any ideas on how to get it to work? ](*,)

I have a remote control that works with TVtime so I want this to work.
I have tried changing settings in alsamixer while playing tvtime, but still no sound.

---

### Post by Jaxilian on 2006-08-08
Solved! I finally got sound. It was the alsamixer that caused it.

---

### Post by nikoPSK on 2007-10-30
what dod you do? i have a !winfast TV2000 XP series and I got the picture but no sound. I don't know what to do. And I have tried unmuting everything in alsamixer....

---

