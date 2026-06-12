---
title: "Mplayer Problem"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by Bofur on 2007-02-04
Hi, I'm trying to play .mpgs and .wmvs on my newly installed mplayer but when I try I get this message:
```
justin@justin-xt41fi7:~$ gmplayer
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T7200  @ 2.00GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.



Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.

Playing /home/justin/Desktop/clip2.wmv.
ASF file format detected.
VIDEO:  [WMV3]  512x288  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 65.1 kbit/4.61% (ratio: 8134->176400)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
open: No such file or directory
Couldn't open: /dev/mga_vid
Error opening/initializing the selected video_out (-vo) device.

```
Does anyone know how to fix this? Thanks!

---

### Post by bom28 on 2007-02-04
Try choosing another video driver in the video tab of the preferences dialog.

---

### Post by Bofur on 2007-02-04
Got it, thanks.

---

### Post by Jose Catre-Vandis on 2007-02-08
Thanks - chose x11 for video and had to set ffmpeg libavcodecs for audio to get everything playing

---

