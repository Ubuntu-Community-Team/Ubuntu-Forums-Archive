---
title: "broken video output"
date: 2008-01-13
forum: Multimedia &amp; Video
---

### Post by lian1238 on 2008-01-13
I don't know how to explain the problem, so there's a screenshot of what the video output looks like when it is broken.

It usually breaks when I pause the video for too long. When I resume, the output looks like the following screenshot. The audio still plays, though. Once it breaks, it is broken for every player and I have to restart X to get it working again.

Anyone ever experience this?

---

### Post by Psykotik on 2008-02-11
I experiment exactly same issue since... i don't remember, maybe before Gutsy.

I don't have any clue on how to debug this bug, since it appear (for what I understand) randomly.

I use nvidia drivers 100.14.19, with a dual desktop (no xinerama, true dual) enabled.

I suspect it is something related to the driver, since restarting compiz doesn't help.

---

### Post by Psykotik on 2008-02-11
I temporarily bypass the issue following some advices you gave on 

[http://ubuntuforums.org/showthread.php?t=671994](http://ubuntuforums.org/showthread.php?t=671994)

by changing settings on vlc and mplayer (mplayer output video from "xv" to "gl2" and vlc output video from "predefined" to "X11 output video").

However, it doesn't seem to be an acceptable solution, especially if I don't know WHY it behaves like that.

Here is the log when gmplayer is set up to "gl2" :

```
$ gmplayer test.avi 
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 4, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /Misc/test.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DX50]  720x368  24bpp  25.000 fps  707.0 kbps (86.3 kbyte/s)
==========================================================================
Trying to force video codec driver family null...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 96.0 kbit/6.25% (ratio: 12000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 368 (preferred colorspace: Planar YV12)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.96:1 - prescaling to correct movie aspect.
[swscaler @ 0x8925250]SwScaler: using unscaled yuv420p -> bgr24 special converter
VO: [gl2] 720x368 => 720x368 BGR 24-bit 
[gl2] You have OpenGL >= 1.2 capable drivers, GOOD (16bpp and BGR is ok!)
[gl2] antialiasing off
[gl2] bilinear linear

```

and there when on "xv" (default) :

```
$ gmplayer test.avi
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.80GHz (Family: 15, Model: 4, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /Misc/test.avi.
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [DX50]  720x368  24bpp  25.000 fps  707.0 kbps (86.3 kbyte/s)
==========================================================================
Trying to force video codec driver family null...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 96.0 kbit/6.25% (ratio: 12000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 368 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.96:1 - prescaling to correct movie aspect.
VO: [xv] 720x368 => 720x368 Planar YV12 
A:  79.7 V:  79.7 A-V:  0.004 ct:  0.006 1994/1994  3%  3%  1.3% 6 0            
Exiting... (Quit)

```

---

### Post by Psykotik on 2008-02-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/162588](https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/162588) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Maybe the answer:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/162588](https://bugs.launchpad.net/ubuntu/+source/nvidia-kernel-common/+bug/162588)

It still need confirmation from people who have actually upgraded nvidia drivers... which is not my case.

---

