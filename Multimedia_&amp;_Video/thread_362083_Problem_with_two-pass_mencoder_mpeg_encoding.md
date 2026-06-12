---
title: "Problem with two-pass mencoder mpeg encoding"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by LucasLinard on 2007-02-15
HI. I try to do a two pass encode with mencoder, form avi to mpeg i use the following command:
##1pass
mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf crop=640:480,scale=720:480,expand=720:576,harddup -srate 48000 -af lavcresample=48000 -lavcopts turbo:vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=2300:keyint=18:vstrict=0:acodec=ac3:abitrate=192:aspect=4/3:border_mask=0.5:dark_mask=0.3:vpass=1 -ofps 24000/1001 -o "/dev/null" "[omda]_X_TV_00.avi"
##2pass
 mencoder -oac lavc -ovc lavc -of mpeg -mpegopts format=dvd:tsaf -vf crop=640:480,scale=720:480,expand=720:576,harddup -srate 48000 -af lavcresample=48000 -lavcopts vcodec=mpeg2video:vrc_buf_size=1835:vrc_maxrate=9800:vbitrate=2300:keyint=18:vstrict=0:acodec=ac3:abitrate=192:aspect=4/3:border_mask=0.5:dark_mask=0.3:vpass=2 -ofps 24000/1001 -o "X_03.mpg" "[omda]_X_TV_03.avi"

at the second command I get the folowind output:
> 
MEncoder 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) XP 2400+ (Family: 6, Model: 8, Stepping: 1)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0xadbc800
AVI file format detected.
VIDEO:  [XVID]  640x480  24bpp  23.976 fps  891.8 kbps (108.9 kbyte/s)
[V] filefmt:3  fourcc:0x44495658  size:640x480  fps:23.98  ftime:=0.0417
==========================================================================
Requested audio codec family [mp3] (afm=mp3lib) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 127.7 kbit/9.05% (ratio: 15963->176400)
Selected audio codec: [ffmp3] afm: ffmpeg (FFmpeg MPEG layer-3 audio decoder)
==========================================================================
PACKET SIZE: 2048 bytes, deltascr: 43885
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
Opening video filter: [harddup]
Opening video filter: [expand w=720 h=576]
Expand: 720 x 576, -1 ; -1, osd: 0, aspect: 0.000000, round: 1
Opening video filter: [scale w=720 h=480]
Opening video filter: [crop w=640 h=480]
Crop: 640 x 480, -1 ; -1
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
Limiting audio preload to 0.4s.
Increasing audio density to 4.
VDec: vo config request - 640 x 480 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.

SwScaler: BICUBIC scaler, from Planar YV12 to Planar YV12 using MMX2
videocodec: libavcodec (720x576 fourcc=3267706d [mpg2])
[mpeg2video @ 0x87bb7ec]Error: 2pass curve failed to converge
Could not open codec.
FATAL: Cannot initialize video driver.

Exiting...

Can someone help???

---

### Post by LucasLinard on 2007-02-16
Thanks to Giacomo Comes
"From: Giacomo Comes

That was a problem of pre8. Upgrade to rc1 or svn."

---

