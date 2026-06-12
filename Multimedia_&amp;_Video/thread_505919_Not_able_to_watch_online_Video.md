---
title: "Not able to watch online Video"
date: 2007-07-20
forum: Multimedia &amp; Video
---

### Post by ascii79 on 2007-07-20
Hi

When I do 

mplayer mms://209.11.242.218/DesiTVShow.COM-StarPlusTV-99sdwsssdwdds0

I am not able to watch video's but it works fine in windows.

Please help.


Regards,
Sachin.

---

### Post by fdrake on 2007-07-20
have you tried with totem
$totem mms://209.11.242.218/DesiTVShow.COM-StarPlusTV-99sdwsssdwdds0

mplayer doesn't work on my comp. but totem does , probably is a codec or a plug-in issue

---

### Post by ascii79 on 2007-07-23
Thanks for the update.

But it get stuck at 10 sec pointer.
Whereas in windows I am able to see the live stream ..

---

### Post by sdowney717 on 2007-07-23
I tried it and it seems to be a short file, but I did see an introduction

scott@scott-desktop:~$ mplayer mms://209.11.242.218/DesiTVShow.COM-StarPlusTV-99sdwsssdwdds0
MPlayer 2:1.0~rc1-0ubuntu9.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.00GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing mms://209.11.242.218/DesiTVShow.COM-StarPlusTV-99sdwsssdwdds0.
STREAM_ASF, URL: mms://209.11.242.218/DesiTVShow.COM-StarPlusTV-99sdwsssdwdds0
Resolving 209.11.242.218 for AF_INET6...
Couldn't resolve name for AF_INET6: 209.11.242.218
Connecting to server 209.11.242.218[209.11.242.218]: 1755...
Connected
unknown object
unknown object
file object, packet length = 1444 (1444)
unknown object
unknown object
stream object, stream ID: 1
stream object, stream ID: 2
unknown object
data object
mmst packet_length = 1444
Cache size set to 64 KBytes
Cache fill: 12.50% (8192 bytes)   
ASF file format detected.
VIDEO:  [WMV1]  208x160  24bpp  20.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
It seems there is no Xvideo support for your video card available.
Run 'xvinfo' to verify its Xv support and read DOCS/HTML/en/video.html#xv!
See 'mplayer -vo help' for other (non-xv) video out drivers. Try -vo x11
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv1] vfm: ffmpeg (FFmpeg M$ WMV1/WMV7)
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 22050 Hz, 2 ch, s16le, 32.0 kbit/4.54% (ratio: 4006->88200)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 208 x 160 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [x11] 208x160 => 208x160 Planar YV12 
SwScaler: using unscaled yuv420p -> rgb32 special converter
Everything done. Thank you for downloading a media file containing proprietary and patented technology.
A:  13.0 V:  13.0 A-V: -0.007 ct: -0.031  10/ 10  2%  0% 10.5% 0 0 0% 

Exiting... (End of file)
scott@scott-desktop:~$

---

### Post by ascii79 on 2007-07-23
Try running the same thing in media player on windows.. 
Then you might see the difference...

---

### Post by ascii79 on 2007-11-06
problem solved in gutsy ...

---

