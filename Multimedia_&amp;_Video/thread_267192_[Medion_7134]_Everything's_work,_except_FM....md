---
title: "[Medion 7134] Everything's work, except FM..."
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by SysterNeoX on 2006-09-28
Hi!
I've got this TV card, wich TV works but FM and Teletext not?
I hear only a noise when i try to use radio in any radio program (gnomeradio,gkrellm and so on), and the program didn't find any radio station.

The dmesg didn't show any problem:

```
[17179587.424000] saa7130/34: v4l2 driver version 0.2.14 loaded
[17179587.596000] saa7134[0]: found at 0000:01:09.0, rev: 1, irq: 201, latency: 32, mmio: 0xe6001000
[17179587.596000] saa7134[0]: subsystem: 16be:0003, board: Medion 7134 [card=12,autodetected]
[17179587.596000] saa7134[0]: board init: gpio is 0
[17179587.732000] saa7134[0]: i2c eeprom 00: be 16 03 00 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17179587.732000] saa7134[0]: i2c eeprom 10: ff ff ff ff 15 00 0e 01 03 c0 08 00 00 00 00 00
[17179587.732000] saa7134[0]: i2c eeprom 20: 00 00 00 da ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.732000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.732000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.732000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.732000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.732000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179587.748000] saa7134[0] Tuner type is 5
[17179587.792000] tuner 2-0060: chip found @ 0xc0 (saa7134[0])
[17179587.912000] saa7134[0]: registered device video0 [v4l2]
[17179587.912000] saa7134[0]: registered device vbi0
[17179587.912000] saa7134[0]: registered device radio0
[17179587.924000] saa7134 ALSA driver for DMA sound loaded
[17179587.924000] saa7134[0]/alsa: saa7134[0] at 0xe6001000 irq 201 registered as card -1

```

I've tried to change device in configuration of gnomeradio to /dev/radio0, /dev/video0, /dev/vbi0 - no luck.

What's wrong?? How to resolve problem??

---

