---
title: "pixelview playTV pro 3 FM radio tuner not registered"
date: 2010-04-17
forum: Multimedia Software
---

### Post by desired on 2010-04-17
ihave ubuntu 9.10 karmic koala and then upgraded to 10.4 lucid lynx.
in karmic my playTV pro3 can works  but after upgraded to lucid my FM tuner doesnot detected
dmesg 
```

.......................................................
[ xx.xxxxxx] saa7130[0]: registered device video0 [v4l2]
[ xx.xxxxxx] saa7130[0]: registered device vbi0
.......................................................

```they should be.. (in karmic before)
```

.......................................................
[ xx.xxxxxx] saa7130[0]: registered device video0 [v4l2]
[ xx.xxxxxx] saa7130[0]: registered device vbi0
[ xx.xxxxxx] saa7130[0]: registered device radio0
.......................................................

```please help. thanks

my pixelView playTV pro 3 can works in Xp Windows, both TV and FM tuner.
sorry my English

---

### Post by desired on 2010-04-17
up :confused:

---

### Post by desired on 2010-04-20
yay... finally got it work
i create saa7134.conf file inside ***/etc/modprobe.d/*** directory, and then add with a line,
```
options saa7134 card=42 tuner=38 gbuffers=4
```dmesg | grep 'saa'
```
[   14.940388] saa7130/34: v4l2 driver version 0.2.15 loaded
[   14.940465] saa7134 0000:02:03.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.940475] saa7130[0]: found at 0000:02:03.0, rev: 1, irq: 16, latency: 32, mmio: 0xfb004000
[   14.940485] saa7130[0]: subsystem: 1131:0000, board: LifeView FlyVIDEO3000 [card=2,insmod option]
[   14.940508] saa7130[0]: board init: gpio is 60c000
[   14.940512] saa7130[0]: there are different flyvideo cards with different tuners
[   14.940514] saa7130[0]: out there, you might have to use the tuner=<nr> insmod
[   14.940516] saa7130[0]: option to override the default value.
[   14.940801] input: saa7134 IR (LifeView FlyVIDEO30 as /devices/pci0000:00/0000:00:1e.0/0000:02:03.0/input/input6
[   14.941004] IRQ 16/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   15.044264] saa7130[0]: Huh, no eeprom present (err=-5)?
[   15.181484] saa7130[0]: i2c scan: found device @ 0xc0  [tuner (analog)]
[   15.472342] tuner 2-0060: chip found @ 0xc0 (saa7130[0])
[   15.704228] saa7130[0]: registered device video0 [v4l2]
[   15.704274] saa7130[0]: registered device vbi0
[   15.704317] saa7130[0]: registered device radio0
[   15.734860] saa7134 ALSA driver for DMA sound loaded
[   15.734868] saa7130[0]/alsa: LifeView FlyVIDEO3000 doesn't support digital audio
```although still output warning, i can listen favor channel...

---

