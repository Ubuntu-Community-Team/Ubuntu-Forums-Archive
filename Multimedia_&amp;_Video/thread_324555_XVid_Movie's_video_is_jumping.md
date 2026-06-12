---
title: "XVid Movie's video is jumping"
date: 2006-12-23
forum: Multimedia &amp; Video
---

### Post by Starcraftmazter on 2006-12-23
As the title says.

I have downloaded 3 videos, all encoded in xvid. The first one seems to work fine, though it's small resolution and low quality (not a fault of any software, thats how it is).

The other two, which are your standard 1.35GB xvid movies, have the video jumping and bouncing in playback.

I have tired in both totem-gstreamer and mplayer, same problem.

I have installed these packages:
[https://help.ubuntu.com/ubuntu/desktopguide/C/codecs.html](https://help.ubuntu.com/ubuntu/desktopguide/C/codecs.html)

I have done the DVD playback thing here:
[https://help.ubuntu.com/ubuntu/desktopguide/C/video.html#dvdplayback](https://help.ubuntu.com/ubuntu/desktopguide/C/video.html#dvdplayback)

And I've also installed the win32codecs pack.

And all that had no effect.

Any suggestions?

---

### Post by pay on 2006-12-24
Maybe they are jumping because that is how they were encoded, or they came from a bad source. I personally use ffmpeg (libavcodec) for decoding with mplayer.

---

### Post by Starcraftmazter on 2006-12-24
I've burned both files to a dvd, and the dvd player plays them perfectly, so it's definately not a problem with the files themselves.

I have installed ffmpeg, using synaptic.

---

### Post by pay on 2006-12-24
It might be a driver issue. You might need to install the driver for your video card or change the driver that mplayer users with```
nano .mplayer/gui.conf
```Also play the video with```
mplayer /path/to/video.avi
```and that will tell you about any problems ie if your cpu isn't fast enough for the high bitrate.

---

### Post by Starcraftmazter on 2006-12-24
How exactly do I choose the driver mplayer uses?

As for cpu power, that's not the case, as videos of the same type worked fine on windows (so long as they were played by divx player, because wmp is bloatware).

I get this when running the video from terminal, as you suggested. I exited when it began playing.

> MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Tualatin (Family: 6, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.


91 audio & 204 video codecs
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
Playing /home/max/my_docs/video/kisa/Puschkin.avi.
AVI file format detected.
VIDEO:  [XVID]  672x368  12bpp  25.000 fps  1384.5 kbps (169.0 kbyte/s)
Clip info:
 Software: VirtualDubMod 1.5.4.1 (build 2178/release)
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
AC3: 5.0 (3f+2r)  48000 Hz  448.0 kbit/s
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Building audio filter chain for 48000Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 48000 Hz/2 channels/4 bpf/65536 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 48000Hz/2ch/s16le -> 48000Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 672 x 368 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.83:1 - prescaling to correct movie aspect.
VO: [xv] 672x368 => 672x368 Planar YV12
alsa-space: xrun of at least 5.819 msecs. resetting stream?,?% 1 0
alsa-space: xrun of at least 0.229 msecs. resetting stream2.0% 22 0
alsa-space: xrun of at least 0.225 msecs. resetting stream1.9% 25 0
alsa-uninit: pcm closed 0.004 ct: -0.025  61/ 61 32% 10%  1.7% 20 0


Thanks.

---

### Post by zgornel on 2006-12-24
> How exactly do I choose the driver mplayer uses?

```
 mplayer -vo **xv** file.avi
```  You can replace **xv** with **x11**, **opengl** etc. If using the **x11** driver, use the **-zoom** option to enable fullscreen

---

