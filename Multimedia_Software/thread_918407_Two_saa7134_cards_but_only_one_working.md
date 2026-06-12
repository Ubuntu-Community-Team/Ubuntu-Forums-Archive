---
title: "Two saa7134 cards but only one working"
date: 2008-09-12
forum: Multimedia Software
---

### Post by chathura on 2008-09-12
Hi guys, I have installed two msi tv@nytime cards to a machine that is running hardy. I m in the need of recording two video streams captured by those two cards. but I was only able to interface one card. the other card is not recognized. 
[U]
***lspci*** returned [/U]
[PHP]
03:00.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
03:02.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
[/PHP]

but when i used _**dmesg | grep saa7134**_
[PHP]
[   34.262069] saa7134[0]: found at 0000:03:00.0, rev: 1, irq: 16, latency: 64, mmio: 0xfe6ff800
[   34.262074] saa7134[0]: subsystem: 1462:8803, board: Philips Tiger reference design [card=81,insmod option]
[   34.262081] saa7134[0]: board init: gpio is c0407f
[   34.402066] saa7134[0]: i2c eeprom 00: 62 14 03 88 10 28 ff ff ff ff ff ff ff ff ff ff
[   34.402074] saa7134[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.402081] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.402087] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.402094] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.402100] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.402107] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.402113] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   34.559268] tuner 0-0060: chip found @ 0xc0 (saa7134[0])
[   34.567237] tuner 0-0061: chip found @ 0xc2 (saa7134[0])
[   34.921921] saa7134[0]: registered device video0 [v4l2]
[   34.921938] saa7134[0]: registered device vbi0
[   34.921952] saa7134[0]: registered device radio0
[   34.921987] saa7134[1]: found at 0000:03:02.0, rev: 1, irq: 18, latency: 64, mmio: 0xfe6ffc00
[   34.921992] saa7134[1]: subsystem: 1462:8803, board: UNKNOWN/GENERIC [card=0,autodetected]
[   34.921998] saa7134[1]: board init: gpio is c0407f
[   35.039213] tuner 1-0060: chip found @ 0xc0 (saa7134[1])
[   35.046170] tuner 1-0061: chip found @ 0xc2 (saa7134[1])
[   35.078115] saa7134[1]: i2c eeprom 00: 62 14 03 88 10 28 ff ff ff ff ff ff ff ff ff ff
[   35.078124] saa7134[1]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   35.078131] saa7134[1]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   35.078139] saa7134[1]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   35.078146] saa7134[1]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   35.078154] saa7134[1]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   35.078161] saa7134[1]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   35.078169] saa7134[1]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   35.078228] saa7134[1]: registered device video1 [v4l2]
[   35.078244] saa7134[1]: registered device vbi1
[   35.136886] saa7134 ALSA driver for DMA sound loaded
[   35.136902] saa7134[0]/alsa: saa7134[0] at 0xfe6ff800 irq 16 registered as card -2
[   35.137105] saa7134[1]/alsa: saa7134[1] at 0xfe6ffc00 irq 18 registered as card -1
[   35.157461] saa7134[0]/dvb: frontend initialization failed

[/PHP]
I modified  ***/etc/modprobe.d/options***  by adding 
[PHP]
options saa7134 card=81 tuner=54

[/PHP]

in addition I modified ***/etc/modules*** by adding
[PHP]
options saa7134 card=81
[/PHP]

but still only one card is working via tvtime or anyother application via /dev/video0. Eventhough I changed /dev/video1 as the source tvtime doesnot respond.in addition I cannot get the video from video0 source.

So guys Im really greatful to you if you can help me with this situation.

Thanks & best reagads.

---

