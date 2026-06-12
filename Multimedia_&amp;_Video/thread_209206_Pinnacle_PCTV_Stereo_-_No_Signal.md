---
title: "Pinnacle PCTV Stereo - No Signal"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by pump on 2006-07-04
I'm sorry if there are some similar topics, but i can't find the solution for this. I have a Pinnacle PCTV Stereo card (SAA7134 Chip and the tuner is a MT2050).
I have this module running with this options:
```
modprobe saa7134 card=26 tuner=33 oss=1
```

The problem comes when I want to use the TV input (actually the SVIDEO and RCA inputs are working). It seems that there is a problem of frecuencies or something like that. I'm in Argentina and here the tv is PAL-N. The other day I could see some channels in black and white (NTSC) but when I switched to PAL the image dissapeared.

Here I add some more information:
Dmesg
```
[4300870.685000] saa7130/34: v4l2 driver version 0.2.14 loaded
[4300870.685000] ACPI: PCI Interrupt 0000:02:0c.0[A] -> GSI 20 (level, low) -> IRQ 217
[4300870.685000] saa7133[0]: found at 0000:02:0c.0, rev: 16, irq: 217, latency: 64, mmio: 0xfeafb000
[4300870.685000] saa7133[0]: subsystem: 11bd:002b, board: Pinnacle PCTV Stereo (saa7134) [card=26,insmod option]
[4300870.685000] saa7133[0]: board init: gpio is 0
[4300870.788000] tda9887 0-0043: chip found @ 0x86 (saa7133[0])
[4300870.796000] tuner 0-0060: Chip ID is not zero. It is not a TEA5767
[4300870.796000] tuner 0-0060: chip found @ 0xc0 (saa7133[0])
[4300870.803000] tuner 0-0060: microtune: companycode=3cbf part=42 rev=26
[4300870.811000] tuner 0-0060: microtune MT2050 found, OK
[4300870.836000] saa7133[0]: i2c eeprom 00: bd 11 2b 00 f8 f8 1c 00 43 43 a9 1c 55 d2 b2 92
[4300870.836000] saa7133[0]: i2c eeprom 10: 00 00 19 0e ff 20 ff ff ff ff ff ff ff ff ff ff
[4300870.836000] saa7133[0]: i2c eeprom 20: 01 40 01 03 03 ff 03 01 08 ff 00 53 ff ff ff ff
[4300870.836000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4300870.837000] saa7133[0]: i2c eeprom 40: ff 07 00 c0 86 ff 01 02 ff ff ff ff ff ff ff ff
[4300870.837000] saa7133[0]: i2c eeprom 50: 0c 22 17 0a 02 13 0a 78 ff ff ff ff ff ff ff ff
[4300870.837000] saa7133[0]: i2c eeprom 60: 03 03 19 71 fb ff ff ff ff ff ff ff ff ff ff ff
[4300870.837000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[4300870.885000] saa7133[0]: registered device video0 [v4l2]
[4300870.886000] saa7133[0]: registered device vbi0

```

lspci
```
0000:02:0c.0 Multimedia controller: Philips Semiconductors SAA7133 Video Broadcast Decoder (rev 10)

```

Thank you in advance, if I can make this work then I'll migrate totally to Ubuntu.

---

### Post by pump on 2006-07-05
Now it seems that when I switch to Windows it doesn't have signal neither. I have to turn the computer off and then it'll work (in Windows).
It seems to be a problem with the tuner. Does somebody knows?

---

