---
title: "Sound only on one side in radio tv/fm card"
date: 2009-06-11
forum: Multimedia Software
---

### Post by demikid on 2009-06-11
Hi guys. I have this tv/fm card which works perfectly with tvtime i.e.picture works fine and sound comes out from both sides of my speakers. Trouble is,when listening to fm radio with kradio,gradio etc sound comes only from one side. Somebody help?

This is my dmesg output:
[INDENT][   11.210396] saa7130[0]: subsystem: 4e42:0138, board: LifeView/Typhoon FlyVIDEO2000 [card=3,autodetected]
[   11.210439] saa7130[0]: board init: gpio is 39100
[   11.210444] saa7130[0]: there are different flyvideo cards with different tuners
[   11.210445] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[   11.210447] saa7130[0]: option to override the default value.
[   11.210597] input: saa7134 IR (LifeView/Typhoon Fl as /devices/pci0000:00/0000:00:1e.0/0000:02:07.0/input/input6
[   11.360016] saa7130[0]: i2c eeprom 00: 42 4e 38 01 10 28 ff ff ff ff ff ff ff ff ff ff
[   11.360034] saa7130[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360047] saa7130[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360060] saa7130[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360073] saa7130[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360085] saa7130[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360098] saa7130[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360111] saa7130[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360124] saa7130[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360137] saa7130[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360150] saa7130[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360162] saa7130[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360175] saa7130[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360188] saa7130[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360201] saa7130[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.360214] saa7130[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   11.397775] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.397873] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   11.412022] tuner' 0-0061: chip found @ 0xc2 (saa7130[0])
[   11.420011] tuner' 0-0063: chip found @ 0xc6 (saa7130[0])
[   11.476015] tuner-simple 0-0061: creating new instance
[   11.476023] tuner-simple 0-0061: type set to 69 (Tena TNF 5335 and similar models)
[   11.500169] saa7130[0]: registered device video0 [v4l2]
[   11.500246] saa7130[0]: registered device vbi0
[   11.500325] saa7130[0]: registered device radio0
[   11.514485] saa7134 ALSA driver for DMA sound loaded
[   11.514527] saa7130[0]/alsa: saa7130[0] at 0xfebffc00 irq 23 registered as card -2
[   11.720019] intel8x0_measure_ac97_clock: measured 54719 usecs
[   11.720024] intel8x0: clocking to 48000
[   11.874173] lp0: using parport0 (interrupt-driven).
[/INDENT]

output from lshw -C multimedia
[INDENT]*-multimedia
       description: Multimedia controller
       product: SAA7130 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 7
       bus info: pci@0000:02:07.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=248 maxlatency=40 mingnt=16 module=saa7134
  *-multimedia
       description: Multimedia audio controller
       product: 82801G (ICH7 Family) AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1e.2
       bus info: pci@0000:00:1e.2
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0
[/INDENT]

---

