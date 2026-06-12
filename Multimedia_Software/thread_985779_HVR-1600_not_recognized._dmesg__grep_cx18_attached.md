---
title: "HVR-1600 not recognized. dmesg | grep cx18 attached"
date: 2008-11-17
forum: Multimedia Software
---

### Post by Vidar Brekke on 2008-11-17
Just installed a fresh copy of Ubuntu Intrepid Ibex to run my MythTV backend. Went out and bough an Hauppauge HVR-1600 capture card -but I'm having a hard time getting it to install and be recognized by the system. What am I doing wrong and how can I fix it. I'm a relatively newbie to Linux.

I've followed the instructions here: [http://www.ivtvdriver.org/index.php/Cx18](http://www.ivtvdriver.org/index.php/Cx18)

but when I issue "dmesg | grep cx18", this is what I get:

[   29.567357] cx18:  Start initialization, version 1.0.2
[   29.567432] cx18-0: Initializing card #0
[   29.567437] cx18-0: Autodetected Hauppauge card
[   29.568518] cx18 0000:04:06.0: PCI INT A -> Link[APC3] -> GSI 18 (level, low) -> IRQ 18
[   29.568531] cx18-0: Unreasonably low latency timer, setting to 64 (was 32)
[   29.574859] cx18-0: cx23418 revision 01010000 (B)
[   30.082224] cx18-0: Invalid EEPROM
[   30.082228] cx18-0: VBI is not yet supported
[   30.719518] cs5345 2-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   30.725305] cx18-0: Disabled encoder IDX device
[   30.725457] cx18-0: Registered device video0 for encoder MPEG (2 MB)
[   30.725462] DVB: registering new adapter (cx18)
[   30.870672] cx18-0: frontend initialization failed
[   30.871033] cx18-0: DVB failed to register
[   30.871128] cx18-0: Registered device video32 for encoder YUV (2 MB)
[   30.871196] cx18-0: Registered device video24 for encoder PCM audio (1 MB)
[   30.871263] cx18-0: Registered device radio0 for encoder radio
[   30.871691] cx18-0: Error -1 registering devices
[   30.872479] cx18-0: Error -1 on initialization
[   30.872497] cx18: probe of 0000:04:

---

