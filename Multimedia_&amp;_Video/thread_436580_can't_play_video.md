---
title: "can't play video"
date: 2007-05-08
forum: Multimedia &amp; Video
---

### Post by dummies85 on 2007-05-08
i just downloaded a video file, the video codec is ITU H.264 and audio codec MPEG-1 layer 3.  Everytime i play the video the player suddenly closed, i've tried totem, xine, gxine, and VLC all of them give the same reaction, is there a way so i can play the video normally?

---

### Post by jiminycricket on 2007-05-08
Try playing it with mplayer in the command line and post output to Launchpad

Also, use debuggers and apport to trace why it crashed and post to launchpad.  Does apport start up after it crashe?  Are you using Feisty Fawn?

---

### Post by dummies85 on 2007-05-08
yes i'm using feisty, and after the player closed nothing happened, was apport suppose to show after the player closed?
here is the message i get after playing the video with command line

> MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 8)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing One_Piece_296.avi.
AVI file format detected.
VIDEO:  [H264]  1280x720  24bpp  23.976 fps  1584.9 kbps (193.5 kbyte/s)
Clip info:
 Source: D-CX(D3Cap)
 Creation Date: 07/02/05
 Genre: anime
 Software: aviutl98d
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffh264] vfm: ffmpeg (FFmpeg H.264)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 1280 x 720 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
X11 error: BadAlloc (insufficient resources for operation)?,?% 0 0 


MPlayer interrupted by signal 6 in module: vo_check_events
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

which part of the code i should post? and i don't really understand how to debug, where can i learn to use one?

---

### Post by honghai on 2007-05-08
which graphic card do you use? I had the same problem with my intel 915 card. And my solution is to use the new drivers from debian repository: 
[http://ubuntuforums.org/showthread.php?t=428134&highlight=badalloc](http://ubuntuforums.org/showthread.php?t=428134&highlight=badalloc).

check my reply there.

---

### Post by dummies85 on 2007-05-08
:lolflag: horray!!!!
it worked, thx honhai. i tried using your idea, but i downloaded the intel driver from synaptic and change the xorg.conf in the device section from "i810" to "intel"
by the way, my board is 945express i think, the intel notebook series

---

