---
title: "avi problems in mplayer"
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by legatek on 2008-04-18
Hello,

I am having a problem playing a .avi file in Mplayer (the most up to date version in the feisty repos). I have a file entitled 0001-0075.avi, rendered in Blender in MJPG format. If I launch mplayer from the applications menu, or click on the .avi in Nautilus, Mplayer opens the .avi and plays it upside down (no green stripe like in other threads, just upside down). However, if I launch Mplayer from the command line (mplayer 0001-0075.avi) it plays just fine. Here is the output from the terminal:

```
MPlayer 2:1.0~rc1-0ubuntu9.3 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 2.00GHz (Family: 6, Model: 13, Stepping: 6)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing 0001_0075.avi.
AVI file format detected.
AVI_NI: No audio stream found -> no sound.
AVI: No audio stream found -> no sound.
VIDEO:  [MJPG]  1280x1024  24bpp  25.000 fps  18504.1 kbps (2258.8 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffmjpeg] vfm: ffmpeg (FFmpeg MJPEG decoder)
==========================================================================
Audio: no sound
Starting playback...
VDec: vo config request - 1280 x 1024 (preferred colorspace: Planar 422P)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Planar 422P as output csp (no 1)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8

SwScaler: BICUBIC scaler, from yuv422p to yuv420p using MMX2
SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
SwScaler: 1280x1024 -> 1280x1024
VO: [xv] 1280x1024 => 1280x1024 Planar YV12 
V:   3.0  75/ 75 45% 37%  0.0% 0 0 

Exiting... (End of file)
```

Does anybody know how to fix this so that Mplayer plays .avis correctly regardless of how I choose to open them?

---

### Post by xc3RnbFO8P on 2008-04-18
Try to reinstall mplayer in Synaptic Package Manager.

---

### Post by legatek on 2008-04-18
I tried reinstalling, no change. I tried a complete removal and fresh installation, also no change. Any other ideas?

---

### Post by xc3RnbFO8P on 2008-04-18
Right click on mplayer window, go to preferences and open Video tab and choose driver.
x11  or
x11 OpenGl

---

### Post by legatek on 2008-04-18
The driver was already X11, changing to X11 (Open GL) slowed the speed to around half (which was kind of nice, by the way) but didn't fix the upside down-ness. Other drivers either resulted in no change or a failure to open the file.

Hmm, this is a puzzle, that's for sure.

---

### Post by fatihsanli58 on 2008-06-18
hi, I do not know you tried or not but do this:
1.open mplayer
2.right click
3.preferences
4.video
and check if the 'flip image upsidedown' is marked. if so unmark it. It should work.

---

### Post by ikki_72 on 2008-06-18
why not try deleting the configuration directory. It is a hidden file. If i'm not mistaken its **.mplayer**. What you could do: **Open your home directory** from Nautilus (other if you're not using Gnome) then **press Ctrl + H** to view the hidden files. **Delete .mplayer** then try to **open Mplayer**.

hth.

---

