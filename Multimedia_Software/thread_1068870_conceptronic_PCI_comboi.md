---
title: "conceptronic PCI comboi"
date: 2009-02-13
forum: Multimedia Software
---

### Post by ThL on 2009-02-13
Hi, 

a few days ago I plugged my new conceptronic pci comboi analogue/dvb-t adapter into my amd-64 machine with ubuntu 8.10 intrepid. 
Video works fine, I can get the video on composite and on tv input from my camera, but no audio, whatever I try. 

The dmesg output is: 

```

[   14.642330] saa7130/34: v4l2 driver version 0.2.14 loaded
[   14.643665] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   14.643678] saa7134 0000:04:09.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   14.643684] saa7133[0]: found at 0000:04:09.0, rev: 209, irq: 17, latency: 255, mmio: 0xfdbff000
[   14.643690] saa7133[0]: subsystem: 17de:7201, board: Tevion/KWorld DVB-T 220RF [card=88,autodetected]
[   14.643700] saa7133[0]: board init: gpio is 100
[   14.797021] saa7133[0]: i2c eeprom 00: de 17 01 72 ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797034] saa7133[0]: i2c eeprom 10: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797042] saa7133[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797051] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797059] saa7133[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797067] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797075] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797083] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797091] saa7133[0]: i2c eeprom 80: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797099] saa7133[0]: i2c eeprom 90: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797108] saa7133[0]: i2c eeprom a0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797116] saa7133[0]: i2c eeprom b0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797124] saa7133[0]: i2c eeprom c0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797132] saa7133[0]: i2c eeprom d0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797140] saa7133[0]: i2c eeprom e0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.797148] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   14.929090] tuner' 2-004b: chip found @ 0x96 (saa7133[0])
[   15.021031] tda829x 2-004b: setting tuner address to 61
[   15.101026] tda829x 2-004b: type set to tda8290+75a
[   18.932433] saa7133[0]: registered device video0 [v4l2]
[   18.932483] saa7133[0]: registered device vbi0
[   18.932528] saa7133[0]: registered device radio0
[   18.996535] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 23
[   18.996542] HDA Intel 0000:00:10.1: PCI INT B -> Link[AAZA] -> GSI 23 (level, low) -> IRQ 23
[   18.996561] HDA Intel 0000:00:10.1: setting latency timer to 64
[   19.006320] saa7134 ALSA driver for DMA sound loaded
[   19.006355] saa7133[0]/alsa: saa7133[0] at 0xfdbff000 irq 17 registered as card -2
[   19.121081] DVB: registering new adapter (saa7133[0])
[   19.121088] DVB: registering frontend 0 (Philips TDA10046H DVB-T)...
[   19.221015] tda1004x: setting up plls for 48MHz sampling clock
[   21.476033] tda1004x: timeout waiting for DSP ready
[   21.516032] tda1004x: found firmware revision 0 -- invalid
[   21.516036] tda1004x: trying to boot from eeprom
[   23.848018] tda1004x: timeout waiting for DSP ready
[   23.888016] tda1004x: found firmware revision 0 -- invalid
[   23.888018] tda1004x: waiting for firmware upload...
[   23.888021] firmware: requesting dvb-fe-tda10046.fw
[   36.768018] tda1004x: found firmware revision 20 -- ok

```

Any ideas or experiences? 

Thx in advance, 

Thorsten

---

