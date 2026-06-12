---
title: "[Help] Green screen using TVTime with Pinnacle PCTV 50i"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by subzero1266 on 2007-02-18
Hello everyone,
 I switched to Ubuntu from Win XP just 2 days back. I got everthing working, except have a strange problem with my Pinnacle PCTV 50i tv tuner (which gets detected as 110i in windows also).

I get this green colored corrupted video in TVTime. The sound in the channels is perfect except I dont get to see the actual video as shown in the screenshot below -

[IMG]http://img176.imageshack.us/img176/2952/tvek5.jpg[/IMG]

After installing Ubuntu, I installed nVidia driver and also setup compiz. I didnt enable compiz to run at startup, so I dont think that is making the tv video to show garbage.

This is the output of dmesg for the info -

```
[17179591.080000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179591.080000] ACPI: PCI Interrupt 0000:03:02.0[A] -> GSI 19 (level, low) -> IRQ 217
[17179591.080000] saa7133[0]: found at 0000:03:02.0, rev: 208, irq: 217, latency: 64, mmio: 0xfebff800
[17179591.080000] saa7133[0]: subsystem: 11bd:002e, board: Pinnacle PCTV 110i (saa7133) [card=77,autodetected]
[17179591.080000] saa7133[0]: board init: gpio is 200e000
[17179591.192000] input: Pinnacle PCTV as /class/input/input3
[17179591.232000] saa7133[0]: i2c eeprom 00: bd 11 2e 00 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[17179591.232000] saa7133[0]: i2c eeprom 10: ff e0 60 02 ff 20 ff ff ff ff ff ff ff ff ff ff
[17179591.232000] saa7133[0]: i2c eeprom 20: 01 2c 01 02 02 01 04 30 98 ff 00 a0 ff 22 00 c2
[17179591.232000] saa7133[0]: i2c eeprom 30: 96 ff 03 30 15 01 ff ff 0c 22 17 87 03 45 b8 67
[17179591.232000] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179591.232000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179591.232000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179591.232000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179591.324000] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[17179591.372000] tuner 0-004b: setting tuner address to 61
[17179591.412000] tuner 0-004b: tuner: type set to tda8290+75a
[17179591.556000] saa7133[0]: registered device video0 [v4l2]
[17179591.556000] saa7133[0]: registered device vbi0
[17179591.556000] saa7133[0]: registered device radio0
[17179591.564000] ts: Compaq touchscreen protocol output
[17179591.576000] saa7134 ALSA driver for DMA sound loaded
[17179591.576000] saa7133[0]/alsa: saa7133[0] at 0xfebff800 irq 217 registered as card -1

```

Any help in fixing the green video display is appreciated. Thank you!

---

### Post by kiran_aryan on 2007-02-18
hey subzero, click switch user button. when switching the user, it asks to u choose either standard server or xgl server. choose standard server. now run tvtime and see. hope this helps.

---

### Post by subzero1266 on 2007-02-18
thanks a lot kiran. problem solved. shutting down xgl gave proper display in tvtime :D :D

---

