---
title: "Channel scaning ok, but LiveTV doesn't work"
date: 2008-05-02
forum: Mythbuntu
---

### Post by NarsilAnduril on 2008-05-02
Hi guys,

PVR-500 on a mythbuntu 8.04

Channel scanning returns the correct frequencies, but when I try LiveTV, the black screen of death goes back to GUI after a couple of seconds.

I only see snow in MPlayer opening /dev/video0 and /dev/video1

lspci :
```

03:08.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
	Subsystem: Hauppauge computer works Inc. WinTV PVR 500 (1st unit)
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at d8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [44] Power Management version 2

03:09.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
	Subsystem: Hauppauge computer works Inc. WinTV PVR 500 (2nd unit)
	Flags: bus master, medium devsel, latency 64, IRQ 17
	Memory at dc000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [44] Power Management version 2
```

dmesg|grep ivtv :
```

[   29.542555] ivtv:  Start initialization, version 1.1.0
[   29.542647] ivtv0: Initializing card #0
[   29.542650] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   29.570153] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   29.802168] ivtv0: Autodetected WinTV PVR 500 (unit #1)
[   29.902380] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   29.906443] tuner 0-0060: chip found @ 0xc0 (ivtv i2c driver #0)
[   29.906696] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   29.987779] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   30.010172] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   30.018751] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   30.018766] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   30.018780] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   30.018794] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   30.018808] ivtv0: Registered device radio0 for encoder radio
[   30.018810] ivtv0: Initialized card #0: WinTV PVR 500 (unit #1)
[   30.018872] ivtv1: Initializing card #1
[   30.018875] ivtv1: Autodetected Hauppauge card (cx23416 based)
[   30.019976] ivtv1: Unreasonably low latency timer, setting to 64 (was 32)
[   30.025713] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #1)
[   30.029022] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #1)
[   30.045381] cx25840 1-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #1)
[   30.045629] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #1)
[   30.122724] ivtv1: Correcting tveeprom data: no radio present on second unit
[   30.122726] ivtv1: Autodetected WinTV PVR 500 (unit #2)
[   30.183947] ivtv1: Registered device video1 for encoder MPG (4096 kB)
[   30.183973] ivtv1: Registered device video33 for encoder YUV (2048 kB)
[   30.183998] ivtv1: Registered device vbi1 for encoder VBI (1024 kB)
[   30.184023] ivtv1: Registered device video25 for encoder PCM (320 kB)
[   30.184025] ivtv1: Initialized card #1: WinTV PVR 500 (unit #2)
[   30.187254] ivtv:  End initialization
[   49.573048] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   49.770894] ivtv0: Encoder revision: 0x02060039
[   54.239253] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   54.438004] ivtv1: Encoder revision: 0x02060039

```

Everything's looking fine to me.

What's up doc ?

Diego

---

