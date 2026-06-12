---
title: "Hauppauge pvr 150 and mythtv"
date: 2009-01-27
forum: Multimedia Software
---

### Post by jdahlgren on 2009-01-27
I have some trouble with my Hauppauge pvr 150 and mythtv. Everything seems ok until I start searching for channels and get no signal. 

It worked nice until last week when I reinstalled my server from 8.04 32-bit to 8.10 64-bit. 

 
```

dahlgren@home:~$ dmesg |grep ivtv
[   14.882295] ivtv: Start initialization, version 1.4.0
[   14.883272] ivtv0: Initializing card 0
[   14.883276] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   14.883847] ivtv 0000:01:06.0: PCI INT A -> Link[APC2] -> GSI 17 (level, low) -> IRQ 17
[   14.883858] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   14.936834] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   14.981705] cx25840 0-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   15.090278] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   15.248644] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   15.311502] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   19.247928] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   19.247999] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   19.248081] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   19.248130] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   19.248175] ivtv0: Registered device radio0 for encoder radio
[   19.248177] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   19.248415] ivtv: End initialization
[   29.802498] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   30.000150] ivtv0: Encoder revision: 0x02060039

```

Any one having an idea what to do next?

---

### Post by rbmorse on 2009-01-27
Don't you have to recompile the drivers when you switch kernels?

---

### Post by jdahlgren on 2009-01-27
No upgrade from 8.04 to 8.10 it's a complete install on a new hard drive.

---

### Post by Wogie on 2009-05-26
I have exactly the same problem. Output is identical.

Tried MythTV last night - couldn't 'probe' the card at /dev/video0 (which is the default setting apparently)

Will post back here if I come across anything.[-o<

---

