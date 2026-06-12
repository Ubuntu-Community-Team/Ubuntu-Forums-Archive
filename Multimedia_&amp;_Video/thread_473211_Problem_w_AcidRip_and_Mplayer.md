---
title: "Problem w/ AcidRip and Mplayer"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by the_crowbar on 2007-06-13
I have a Feisty (amd64) system that is up to date with all patches. I have a few vob files I copied from DVDs I am trying to rip to xvid for my myth box. Within ACidRip there is the option to detect the proper crop settings. When I run this mplayer bombs. Here is the actual command and output:
```
AcidRip message - Crop detection in progress... please wait
AcidRip message - Running mplayer -vf cropdetect \/home\/james\/dvd_rips\/the_prestige\/the_prestige\.vob -nosound -vo null -frames 10 -sstep 220 -nocache
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 35, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
Terminal type `unknown' is not defined.

Playing /home/james/dvd_rips/the_prestige/the_prestige.vob.
MPEG-PS file format detected.
VIDEO:  MPEG2  720x480  (aspect 3)  29.970 fps  8000.0 kbps (1000.0 kbyte/s)
Opening video filter: [cropdetect]
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 480 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
Opening video filter: [lavc]
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try adding the scale filter, e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
[mpeg1video @ 0xf04c30]removing common factors from framerate
VO: [null] 720x480 => 854x480 Mpeg PES 
V:   0.0   1/  1 ??% ??% ??,?% 0 0                                              
V:   0.3   2/  2 ??% ??% ??,?% 0 0                                              
VDec: vo config request - 720 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
Could not open codec.
FATAL: Cannot initialize video driver.

FATAL: Could not initialize video filters (-vf) or video output (-vo).


Exiting... (End of file)
AcidRip message - Crop detection failed, is the DVD loaded?

```

If I drop the -vo null from the command it will run (and show the video output while doing crop detection). Can anyone tell me what the problem is?

Thanks,
the_crowbar

---

