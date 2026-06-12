---
title: "Playback issues (log included)"
date: 2009-04-17
forum: Mythbuntu
---

### Post by Lorenzo1985 on 2009-04-17
I'm having playback lag issues as seen below:

... represents loads of them, i skipped a load to make thie vaguely readable.

> MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+ (Family: 15, Model: 107, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Terminal type `unknown' is not defined.

Playing /media/media/Videos/Movies/Flashdance.avi.

Cache fill:  0.00% (0 bytes)
Cache fill:  0.00% (0 bytes)
Cache fill:  0.00% (0 bytes)
Cache fill:  0.00% (0 bytes)
Cache fill:  0.00% (0 bytes)
...
Cache fill:  0.18% (16384 bytes)
Cache fill:  0.18% (16384 bytes)
Cache fill:  0.18% (16384 bytes)
Cache fill:  0.18% (16384 bytes)
Cache fill:  0.18% (16384 bytes)
...
Cache fill:  3.95% (360448 bytes)
AVI file format detected.
[aviheader] Video stream found, -vid 0
[aviheader] Audio stream found, -aid 1
VIDEO:  [XVID]  704x400  24bpp  23.976 fps  1614.0 kbps (197.0 kbyte/s)
Clip info:
 Software: transcode-1.0.7
xscreensaver_disable: Could not find XScreenSaver window.
GNOME screensaver disabled
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 448.0 kbit/29.17% (ratio: 56000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 704 x 400 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.76:1 - prescaling to correct movie aspect.
VO: [xv] 704x400 => 704x400 Planar YV12  [fs] [zoom]


           ************************************************
           **** Your system is too SLOW to play this!  ****
           ************************************************

Possible reasons, problems, workarounds:
- Most common: broken/buggy _audio_ driver
  - Try -ao sdl or use the OSS emulation of ALSA.
  - Experiment with different values for -autosync, 30 is a good start.
- Slow video output
  - Try a different -vo driver (-vo help for a list) or try -framedrop!
- Slow CPU
  - Don't try to play a big DVD/DivX on a slow CPU! Try some of the lavdopts,
    e.g. -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all.
- Broken file
  - Try various combinations of -nobps -ni -forceidx -mc 0.
- Slow media (NFS/SMB mounts, DVD, VCD etc)
  - Try -cache 8192.
- Are you using -cache to play a non-interleaved AVI file?
  - Try -nocache.
Read DOCS/HTML/en/video.html for tuning/speedup tips.
If none of this helps you, read DOCS/HTML/en/bugreports.html.

GNOME screensaver enabled

Exiting... (Quit)


my current default video player is
```
mplayer -fs -zoom -autosync 30 -quiet -vo xv -subfont-text-scale 3 -af volnorm -cache 8912 -cache-min 4 -lavdopts threads=2:fast:skiploopfilter=all -sws 0 %s
```

I copied this off someone else because they said it saved there problems. 

Has anyone got better suggestions?

By the way its a combined frontend, backend.

---

