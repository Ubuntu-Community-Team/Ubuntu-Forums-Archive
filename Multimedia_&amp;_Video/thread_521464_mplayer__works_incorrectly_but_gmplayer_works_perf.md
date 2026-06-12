---
title: "??mplayer  works incorrectly but gmplayer works perfectly"
date: 2007-08-09
forum: Multimedia &amp; Video
---

### Post by levinpluto on 2007-08-09
Just as the title suggests. I can get both video and sound working in gmplayer.
But in mplayer, sound works well while video works terrible. It always shows a blue screen. And I have tried many video types , such as avi, rm, mp4, mpeg4, rmvb. No one can play correctly.

I want to know why.

do I have to add some arguments?
or
do I need to modify the config files?

And I will show you the output of the command :


MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Coppermine,Geyserville (Family: 6, Model: 8, Stepping: 6)
CPUflags: MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing lca2006_tvclip.xvid.avi.
AVI file format detected.
VIDEO: [XVID] 390x288 24bpp 25.000 fps 598.3 kbps (73.0 kbyte/s)
Clip info:
Software: transcode-1.0.1
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 390 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.35:1 - prescaling to correct movie aspect.
VO: [xv] 390x288 => 390x288 Planar YV12 [zoom]
A: 2.3 V: 2.3 A-V: 0.041 ct: -0.007 58/ 58 108% 40% 37.6% 46 0
Exiting... (Quit)

---

