---
title: "No video in movies only sound"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by v3rtigo on 2008-03-07
Hi i have problem with movies in ubuntu, i can hear the audio but can't see the video

i have all codecs installed but still nothing.


output from mplayer:
```

MPlayer 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing videot.avi.
AVI file format detected.
VIDEO:  [XVID]  624x352  24bpp  23.976 fps  1029.0 kbps (125.6 kbyte/s)
Clip info:
 Software: transcode-1.0.5rc4
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 128.0 kbit/8.33% (ratio: 16000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 624 x 352 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.77:1 - prescaling to correct movie aspect.
VO: [xv] 624x352 => 624x352 Planar YV12 
A:   3.3 V:   3.3 A-V:  0.000 ct: -0.003  79/ 79  7%  1%  1.7% 1 0 



```

---

### Post by Superevil on 2008-03-07
I have a similar problem I posted about but mine had something to do with compiz and the effects, when I turn them off the movies pay just fine with them on, I still havent figured it out

---

### Post by toddbmobile on 2008-04-26
Yes, I too have the same problem and it is compiz. If I shake the playing window "wobble effect" while the movie plays you can see the video. I looked for a post with a fix, but have found none. I am running 8.04 now and it did the same thing w/ 7.10.

---

