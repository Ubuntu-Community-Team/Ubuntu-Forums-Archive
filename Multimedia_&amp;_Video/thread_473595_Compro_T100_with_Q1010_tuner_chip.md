---
title: "Compro T100 with Q1010 tuner chip"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by Neil_Mac69 on 2007-06-14
I have been wrestling with a newly acquired Compro T100 (budget!) tuner card (saa7130 with Q1010 tuner chip) without success for the last week of sleepless nights (and threatened divorce!!)

Ubuntu Feisty recogniises the card (a a Compro T200), but demesg returns 

[   37.718278] saa7130[0]: Unexpected tuner type info: d5 in eeprom

I have searched forum after forum, Googled and all but with no luck.  Even reloaded latest download of Ubuntu, then in desperation spent tonight changing tuner type one by one  and testing with tvtime but without success.

Here's the whole response:

neil@HTPC1:~$ dmesg | grep saa
[   37.510012] saa7130/34: v4l2 driver version 0.2.14 loaded
[   37.511570] saa7130[0]: found at 0000:01:0d.0, rev: 1, irq: 18, latency: 208, mmio: 0xfcffec00
[   37.511583] saa7130[0]: subsystem: 185b:c901, board: Compro Videomate DVB-T200 [card=71,autodetected]
[   37.511606] saa7130[0]: board init: gpio is 843f00
[   37.511796] input: saa7134 IR (Compro Videomate DV as /class/input/input3
[   37.718113] saa7130[0]: i2c eeprom 00: 5b 18 01 c9 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[   37.718137] saa7130[0]: i2c eeprom 10: 00 ff 86 0f ff 20 ff ff ff ff ff ff ff ff ff ff
[   37.718158] saa7130[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 88 ff ff ff ff
[   37.718177] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   37.718197] saa7130[0]: i2c eeprom 40: ff d5 00 c4 86 1e ff ff ff ff ff ff ff ff ff ff
[   37.718217] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff cb
[   37.718237] saa7130[0]: i2c eeprom 60: 30 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   37.718256] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   37.718278] saa7130[0]: Unexpected tuner type info: d5 in eeprom
[   37.718477] saa7130[0]: registered device video0 [v4l2]
[   37.718549] saa7130[0]: registered device vbi0
[   38.597434] saa7134 ALSA driver for DMA sound loaded
[   38.597501] saa7130[0]/alsa: saa7130[0] at 0xfcffec00 irq 18 registered as card -2

Any suggestions other than ebaying the card toi a Windows user and buying another card?? :(:(

---

### Post by Dr_Snapid on 2008-06-22
How did you go with this? I have the same card and must admit it isnt great even on windows. Did you get it running on linux?

---

### Post by Neil_Mac69 on 2008-06-22
Gave it away and sold it on Ebay:(!  

Have bought a beyonwiz PVR and am delighted:)!

Good luck & regards!

---

