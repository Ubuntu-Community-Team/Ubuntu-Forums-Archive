---
title: "Video Capture Card no longer working"
date: 2012-01-22
forum: Multimedia Software
---

### Post by Onthax on 2012-01-22
I've got a mythtv setup and am using 2 digital capture cards and an analog, all of them have been working fine for a little over a year.

just recently the SCART - RCA cable going from the foxtel to the Haupagge PVR 150 card stopped working so we went and got a new cable.  All working fine when i plug from Foxtel - TV, but when i plug into the mythbuntu box i dont get any pictures.

I tried using VLC to stream the capture card "/dev/video0" but it just crashes with no error.

I checked the kernel logs and this is what show up, anyone got any ideas?

/var/log/kern.log

```
Jan 23 13:18:07 media kernel: [  608.947625] ivtv0: All encoder YUV stream buffers are full. Dropping data.
Jan 23 13:18:07 media kernel: [  608.947628] ivtv0: Cause: the application is not reading fast enough.
Jan 23 13:23:46 media kernel: [  947.609770] vlc[3926]: segfault at 20 ip b76887e8 sp b43ba770 error 4 in libvlccore.so.4.0.2[b75f2000+e4000]
Jan 23 13:25:27 media kernel: [ 1049.398020] vlc[3984]: segfault at 20 ip b77cb7e8 sp b3401770 error 4 in libvlccore.so.4.0.2[b7735000+e4000]
Jan 23 13:26:32 media kernel: [ 1113.686188] vlc[4005]: segfault at b765e000 ip b771991d sp b4351770 error 4 in libvlccore.so.4.0.2[b7683000+e4000]
Jan 23 13:27:49 media kernel: [ 1190.995238] vlc[4031]: segfault at b769d000 ip b775891d sp b4492770 error 4 in libvlccore.so.4.0.2[b76c2000+e4000]
```

---

### Post by Onthax on 2012-01-24
bump

---

### Post by Onthax on 2012-02-28
reinstalled mythbuntu 10.04 and still have the same issue

and if i do a **dmesg | grep -i ivtv**
i get this

```

[   16.473923] ivtv: Start initialization, version 1.4.1
[   16.473951] ivtv0: Initializing card 0
[   16.473952] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   16.474267] ivtv 0000:06:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   16.474274] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   16.538828] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   16.544605] cx25840 1-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   16.557301] tuner 1-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   16.565473] tuner 1-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   16.567716] wm8775 1-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   16.584327] IRQ 19/ivtv0: IRQF_DISABLED is not guaranteed on shared IRQs
[   16.586296] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   16.586335] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   16.586375] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   16.586411] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   16.586447] ivtv0: Registered device radio0 for encoder radio
[   16.586449] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   16.586486] ivtv: End initialization
[   17.207348] ivtv 0000:06:01.0: firmware: requesting v4l-cx2341x-enc.fw
[   17.233993] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   17.437466] ivtv0: Encoder revision: 0x02060039

```

when i ** cat /dev/video0 > test.mpg ** and  **xine test.mpg** it works fine

but it wont play in mythtv or vlc

anyone have any ideas?

---

