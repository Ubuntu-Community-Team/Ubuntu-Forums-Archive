---
title: "Asus MyCinema P7131"
date: 2006-09-24
forum: Multimedia &amp; Video
---

### Post by DennisFR on 2006-09-24
Hello all,

I have an issue with the Asus MyCinema P7131. I can't seem to get the sound part af this TV tuner to work.

I'm trying to setup a box with MythTV, which works fine now. The only glitch is that what ever program I try, none give sound. (MythTV, xawtv, TV Time). Also tried a suggestion from MythTV: startup xawtv, mute the sound and do a aplay /dev/dsp, but no sound there either.

Has anyone a suggestion? Browsing the net didn't help me much yet..

I'm running 2.6.17.4 kernel.

Dmesg output:
```

[42949390.460000] saa7133[0]: found at 0000:04:09.0, rev: 208, irq: 233, latency: 64, mmio: 0xff8ff000
[42949390.460000] saa7133[0]: subsystem: 1043:4862, board: ASUSTeK P7131 Dual [card=78,autodetected]
[42949390.460000] saa7133[0]: board init: gpio is 0
[42949390.460000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[42949390.460000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[42949390.480000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[42949390.640000] saa7133[0]: i2c eeprom 00: 43 10 62 48 54 20 1c 00 43 43 a9 1c 55 d2 b2 92
[42949390.640000] saa7133[0]: i2c eeprom 10: 00 01 20 00 ff 20 ff ff ff ff ff ff ff ff ff ff
[42949390.640000] saa7133[0]: i2c eeprom 20: 01 40 01 02 03 01 01 03 08 ff 00 d6 ff ff ff ff
[42949390.640000] saa7133[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[42949390.640000] saa7133[0]: i2c eeprom 40: ff 21 00 c2 96 10 03 32 15 00 ff ff ff ff ff ff
[42949390.640000] saa7133[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[42949390.640000] saa7133[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[42949390.640000] saa7133[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[42949390.880000] tuner 0-004b: chip found @ 0x96 (saa7133[0])
[42949390.980000] tuner 0-004b: setting tuner address to 61
[42949391.050000] tuner 0-004b: type set to tda8290+75a
[42949391.200000] saa7133[0]: registered device video0 [v4l2]
[42949391.200000] saa7133[0]: registered device vbi0
[42949391.200000] saa7133[0]: registered device radio0
[42949391.210000] saa7134 ALSA driver for DMA sound loaded
[42949391.210000] saa7133[0]/alsa: saa7133[0] at 0xff8ff000 irq 233 registered as card -1
[42949391.420000] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...

```

Thanks,

Dennis

---

### Post by DennisFR on 2006-09-25
Ok, after a try to recompile a module my whole system crashed.
Anyway, reinstalled Ubuntu and got some sound, only not where I wanted..

When I start tvtime and do an aplay /dev/dsp1 I get the sound I need. Only when I tell Mythtv that the sound must come from /dev/dsp1 I get nothing.

Tried sox, but that seems only to work for oss. Is oss better than alsa? If so, how to unload alsa and load oss?
And is it perhaps better to go for an Hauppage card in stead of this one for sound reasons?

Thanks in advance,

Dennis

---

### Post by startherepodcast on 2007-09-25
You could try entering in a terminal:

```
alsamixer -c[MY_DEVICE_NUMBER]
```

Where MY_DEVICE_NUMBER is your video card. If you only have one sound card this number should be 1 if not try some other numbers (i.e. 2, 3, 4...).

In the screen that comes up turn up the sound channels to max (If you don't see any push tab until you see some).

Hope This Helps,

Adsized

---

