---
title: "KWorld DVB-210 produces video but no sound"
date: 2009-05-10
forum: Multimedia Software
---

### Post by stan potts on 2009-05-10
I am using Ubuntu (wubi) on my normally XP desktop, which has the above tv tuner/capture card installed. My problem is that in TVTime, the only program I have found that can display the composite input without too much work, the video is displayed, but I cannot hear any sound. I have checked the mixer, and everything is unmuted and turned to full, but still no sound.

As I am wanting to archive old video cassettes to DVD/VCD I really do need audio. I live in a PAL area (UK).

Any advice that could get sound working will be brilliant.

Dmesg output relating to card:
```
[   16.000978] saa7130/34: v4l2 driver version 0.2.14 loaded
[   16.001058] saa7134 0000:00:0a.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.001066] saa7133[0]: found at 0000:00:0a.0, rev: 209, irq: 17, latency: 32, mmio: 0xdfffe000
[   16.001074] saa7133[0]: subsystem: 17de:7250, board: KWorld DVB-T 210 [card=114,autodetected]
[   16.001139] saa7133[0]: board init: gpio is 100
[   16.082601] HDA Intel 0000:02:00.1: PCI INT B -> GSI 25 (level, low) -> IRQ 25
[   16.082680] HDA Intel 0000:02:00.1: setting latency timer to 64
[   16.082686] HDA Intel 0000:02:00.1: PCI: Disallowing DAC for device
[   16.136406] HDA Intel 0000:04:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   16.136429] HDA Intel 0000:04:01.0: setting latency timer to 64
[   16.136433] HDA Intel 0000:04:01.0: PCI: Disallowing DAC for device
[   16.152508] saa7133[0]: i2c eeprom 00: de 17 50 72 ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152522] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152535] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152548] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152561] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152574] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152587] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152600] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152613] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152626] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152639] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152652] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152665] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152678] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152691] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.152704] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.165965] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   16.280105] tuner' 1-004b: chip found @ 0x96 (saa7133[0])
[   16.368103] tda829x 1-004b: setting tuner address to 61
[   16.421525] psmouse serio1: ID: 10 00 64<6>tda829x 1-004b: type set to tda8290+75a
[   16.971685] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   20.268487] saa7133[0]: registered device video0 [v4l2]
[   20.268545] saa7133[0]: registered device vbi0
[   20.268596] saa7133[0]: registered device radio0
[   20.347289] saa7134 ALSA driver for DMA sound loaded
[   20.347326] saa7133[0]/alsa: saa7133[0] at 0xdfffe000 irq 17 registered as card -2
[   20.405215] dvb_init() allocating 1 frontend
[   20.440113] DVB: registering new adapter (saa7133[0])
[   20.440119] DVB: registering adapter 0 frontend 0 (Philips TDA10046H DVB-T)...
[   20.512022] tda1004x: setting up plls for 48MHz sampling clock
[   20.539300] lp: driver loaded but no devices found
[   20.800032] tda1004x: found firmware revision 20 -- ok
```

Thanks
Stan

---

### Post by quokka on 2009-05-10
Apologies in advance if I am stating the obvious, but if you are using composite video in, you will also have to connect the RCA audio out from your VCR to the line in on your sound card or motherboard.

Is sound working on your system at all? I noted that there is a message about ALC883 in your dmesg output.

I've done this with Kworld T-100 composite in (different chipset) and it worked without issue.

---

### Post by stan potts on 2009-05-11
Hi. My sound works perfectly well on everything else - wine, firefox (flash), vlc and so on. It is only when using the tv tuner/capture card that it has trouble.

The 2 audio jacks are currently plugged into the red/white RCA in jacks of the capture card. This method works fine in WinXP, so I might have to have video going into capture card, and audio going into sound card?

Thanks

---

