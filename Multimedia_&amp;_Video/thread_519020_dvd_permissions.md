---
title: "dvd permissions"
date: 2007-08-06
forum: Multimedia &amp; Video
---

### Post by xerosis on 2007-08-06
I'm running kubuntu on a new macbook and I've never gotten DVDs to work. It's not a css problem, or any codecs, i think it's a permissions one. here are some details:

**kieran@kieran-laptop:~$ ls -l /dev/dvd**
lrwxrwxrwx 1 root root 4 2007-08-06 19:31 /dev/dvd -> scd0

**kieran@kieran-laptop:~$ ls -l /dev/scd0**
brw-rw---- 1 root cdrom 11, 0 2007-08-06 19:31 /dev/scd0

fstab entry:
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

attempts with mplayer:

**kieran@kieran-laptop:~$ mplayer dvd://**
MPlayer 2:1.0~rc1-0ubuntu11 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://.
Couldn't open DVD device: /dev/dvd
[file] No filename
Failed to open dvd://.


Exiting... (End of file)

**kieran@kieran-laptop:~$ mplayer dvd:///dev/scd0**
MPlayer 2:1.0~rc1-0ubuntu11 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU         T7400  @ 2.16GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd:///dev/scd0.
Option stream url: This URL doesn't have a hostname part.
Couldn't open DVD device: /dev/dvd
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x576  (aspect 2)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
Xv: could not grab port 73
==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
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
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 768x576 Planar YV12
V:   0.0   1/  1 ??% ??% ??,?% 0 0

Exiting... (End of file)


This opens a window, then closes. 

Kaffeine always gives me the error that i do not have enough permissions on the drive.

---

