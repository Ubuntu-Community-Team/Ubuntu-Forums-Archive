---
title: "Problem with mplayer"
date: 2007-06-17
forum: Multimedia &amp; Video
---

### Post by Kagoul on 2007-06-17
Hi, 

Whenever I try to view a video online, or locally mplayer just wouldn't open it, even if I've already  downloaded the w32codecs , here's the error message I get when I try to open an avi file
 
```
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 1.80GHz (Family: 15, Model: 2, Stepping: 4)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mimip2p+nike(XV536).avi.
AVI file format detected.
VIDEO:  [DX50]  640x480  24bpp  29.970 fps  1400.8 kbps (171.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 192.0 kbit/13.61% (ratio: 24000->176400)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 640x480 => 640x480 Planar YV12
[mpeg4 @ 0x8939638]frame skip 8t:  0.000   1/  1 ??% ??% ??,?% 0 0
X11 error: BadAlloc (insufficient resources for operation)?,?% 2 0


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.
```

Any idea what its mean.?? thanx for help..

---

### Post by Gremlinzzz on 2007-06-17
Dont know.I would uninstall delete folder then install smplayer it runs better and plays dvd movies .check it out [http://smplayer.sourceforge.net/](http://smplayer.sourceforge.net/)

---

### Post by shirilover on 2007-06-18
Smplayer is just a qt frontend to mplayer. Chances are that the problem would remain.
About the problem, the only thing I can think of is a corrupted file.

---

### Post by Gremlinzzz on 2007-06-18
That frontend to mplayer will play my DVD movies without frontend to mplayer my mplayer would not.When you install smplayer you have a choice use frontend to mplayer or mplayer.They both install together .also uninstalling and deleteing the mplayer folder should remove a corrupted file..

---

### Post by Kagoul on 2007-06-18
Hello Gremlinzzz & shirilover,

Thanx for your responses, however the file is not corrupted I tried it on another pc under win and it worked fine, I guess it's a codec problem, but I can't find what it is..

---

### Post by Circuit99 on 2007-08-06
You don't say how you setup your codecs, maybe these links may help:


[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


[http://www.medibuntu.org/repository.php](http://www.medibuntu.org/repository.php)

You might need the codecs from Medibuntu

Good Luck

:guitar:

---

