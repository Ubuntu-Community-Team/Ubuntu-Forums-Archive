---
title: "SAA7134 Details help me"
date: 2010-12-06
forum: Multimedia Software
---

### Post by kistareddyd on 2010-12-06
dmesg | grep saa

[   14.464976] saa7130/34: v4l2 driver version 0.2.16 loaded
[   14.465025] saa7134 0000:05:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.465031] saa7134[0]: found at 0000:05:05.0, rev: 1, irq: 21, latency: 16, mmio: 0xfd7ff000
[   14.465036] saa7134[0]: subsystem: 1131:0000, board: Pinnacle PCTV Stereo (saa7134) [card=26,insmod option]
[   14.465056] saa7134[0]: board init: gpio is c04000
[   14.572207] saa7134[0]: Huh, no eeprom present (err=-5)?
[   14.608084] tuner 1-0043: chip found @ 0x86 (saa7134[0])
[   14.636198] tuner 1-0060: chip found @ 0xc0 (saa7134[0])
[   14.696569] saa7134[0]: registered device video0 [v4l2]
[   14.696594] saa7134[0]: registered device vbi0
[   14.702246] saa7134 ALSA driver for DMA sound loaded
[   14.702272] saa7134[0]/alsa: saa7134[0] at 0xfd7ff000 irq 21 registered as card -2

and /etc/modeprob.d/options details:
options saa7134 card=26 tuner=51 alsa=1





When i run tvtime-scan no frequcys found plzz help i am form india-Hyderabad

---

### Post by kistareddyd on 2010-12-06
> **kistareddyd said:**
> dmesg | grep saa

[   14.464976] saa7130/34: v4l2 driver version 0.2.16 loaded
[   14.465025] saa7134 0000:05:05.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   14.465031] saa7134[0]: found at 0000:05:05.0, rev: 1, irq: 21, latency: 16, mmio: 0xfd7ff000
[   14.465036] saa7134[0]: subsystem: 1131:0000, board: Pinnacle PCTV Stereo (saa7134) [card=26,insmod option]
[   14.465056] saa7134[0]: board init: gpio is c04000
[   14.572207] saa7134[0]: Huh, no eeprom present (err=-5)?
[   14.608084] tuner 1-0043: chip found @ 0x86 (saa7134[0])
[   14.636198] tuner 1-0060: chip found @ 0xc0 (saa7134[0])
[   14.696569] saa7134[0]: registered device video0 [v4l2]
[   14.696594] saa7134[0]: registered device vbi0
[   14.702246] saa7134 ALSA driver for DMA sound loaded
[   14.702272] saa7134[0]/alsa: saa7134[0] at 0xfd7ff000 irq 21 registered as card -2

and /etc/modeprob.d/options details:
options saa7134 card=26 tuner=51 alsa=1

When i run tvtime-scan no frequcys found plzz help i am form india-Hyderabad

ok i got picture with good quality but no sound ...i am using ubuntu 10.10 Maverick

---

