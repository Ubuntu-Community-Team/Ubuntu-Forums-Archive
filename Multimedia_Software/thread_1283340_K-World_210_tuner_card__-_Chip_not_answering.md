---
title: "K-World 210 tuner card  - Chip not answering"
date: 2009-10-05
forum: Multimedia Software
---

### Post by picklehead334 on 2009-10-05
Hello, Apologies if i'm going against convention and so on as this is my first post. I've been trying for a few days now to get my K-World 210 dvb Tuner card working with jaunty with a view to getting mythtv working. But currently i cannot even get the card to work with anything. 

As far as i've been able to determine, this card doesn't need firmware loading??? ive loaded the module saa7134, saa7134_dvb and saa7134_alsa and tried some card=x and tuner=y options in modprobe.d but each time I get the following dmesg error: 

```
[ 1353.253855] saa7134 ALSA driver for DMA sound unloaded
[ 1354.925700] saa7130/34: v4l2 driver version 0.2.15 loaded
[ 1354.925780] saa7133[0]: found at 0000:00:0b.0, rev: 209, irq: 19, latency: 32, mmio: 0xee004000
[ 1354.925794] saa7133[0]: subsystem: 17de:7253, board: Philips Tiger reference design [card=81,insmod option]
[ 1354.925854] saa7133[0]: board init: gpio is 200004
[ 1355.076016] saa7133[0]: i2c eeprom 00: de 17 53 72 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[ 1355.076035] saa7133[0]: i2c eeprom 10: ff ff ff 0f ff 20 ff ff ff ff ff ff ff ff ff 01
[ 1355.076050] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 01 01 03 08 ff 00 fe ff ff ff ff
[ 1355.076065] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1355.076080] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 56 ff ff ff ff ff ff
[ 1355.076095] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1355.076110] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1355.076124] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1355.076139] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1355.076154] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1355.076168] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1355.076183] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1355.076198] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1355.076212] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1355.076227] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1355.076242] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[ 1355.085705] saa7133[0]: registered device video0 [v4l2]
[ 1355.085758] saa7133[0]: registered device vbi0
[ 1355.085807] saa7133[0]: registered device radio0
[ 1355.101007] saa7134 ALSA driver for DMA sound loaded
[ 1355.101063] saa7133[0]/alsa: saa7133[0] at 0xee004000 irq 19 registered as card 1
[ 1355.117414] dvb_init() allocating 1 frontend
[ 1355.117849] tda10046: chip is not answering. Giving up.

```

It seems to be working up to the card not responding at some point.

I don't know where to go with this now. I tried downloading the latest v4l with mercurial and building it but that didn't seem to help. 

Any thoughts or help would be greatly appreciated.

---

### Post by picklehead334 on 2009-10-06
No one have any ideas? 

Is the card broken perhaps?

Or do I need firmware?

---

### Post by picklehead334 on 2009-10-06
Ok it seems now after a reboot it is working. Not sure why though. I'll have to see how it goes

---

