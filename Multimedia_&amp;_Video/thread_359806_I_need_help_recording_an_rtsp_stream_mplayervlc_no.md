---
title: "I need help recording an rtsp stream mplayer/vlc not working"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by maddbaron on 2007-02-12
I have attempted to use mplayer and vlc player to record an rtsp stream and nothing is working
this is what I entered in konsole for mplayer
>  ~$ mplayer -noframedrop -dumpfile out.rm -dumpstream rtsp://video.c-span.org/60days/e021007_smiley1.rm

This is what I got
>  MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Mobile AMD Sempron(tm) Processor 3000+ (Family: 15, Model: 28, Stepping: 0)
CPUflags: MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
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

Playing rtsp://video.c-span.org/60days/e021007_smiley1.rm.
STREAM_RTSP, URL: rtsp://video.c-span.org/60days/e021007_smiley1.rm
Resolving video.c-span.org for AF_INET6...
Couldn't resolve name for AF_INET6: video.c-span.org
Resolving video.c-span.org for AF_INET...
Connecting to server video.c-span.org[12.170.145.134]: 554...
Cache size set to 640 KBytes

It just stays there and nothing happens.

I tried using vlc and nothing happened..

Can someone help me please?

---

### Post by Kleist on 2007-02-14
I've been trying for a while to record rm files with mplayer and vlc with not luck. I guess that it's not supported.

---

### Post by slAoD on 2007-09-28
check this:
[http://www.m0interactive.com/archives/2007/07/12/how_to_rip_real_media_rtsp_streams_from_the_web_to_mp3_using_mplayer.html](http://www.m0interactive.com/archives/2007/07/12/how_to_rip_real_media_rtsp_streams_from_the_web_to_mp3_using_mplayer.html)

---

