---
title: "PAFF interlacing is not implemented"
date: 2008-10-01
forum: Multimedia Software
---

### Post by jutirain on 2008-10-01
My new camera use quicktime as video code.
When I use mplayer to play the video it recorded, it's just a mess. (although the color is right)

Since the output of mplayer include the following message:
PAFF interlacing is not implemented
So I google around to find the solution.
I exactly followed the steps of the following page to install the latest ffmpeg:
[http://www.apaddedcell.com/installing-the-latest-ffmpeg-on-ubuntu-feisty-fawn-7-04](http://www.apaddedcell.com/installing-the-latest-ffmpeg-on-ubuntu-feisty-fawn-7-04)
but no help. :(

So, how can I play the video on my Ubuntu 7.04?
I put the video here:
[http://graphics.csie.ntu.edu.tw/~jonathan/ueno/CIMG1096.MOV](http://graphics.csie.ntu.edu.tw/~jonathan/ueno/CIMG1096.MOV)
If some one knows please tell me. I would appreciate that.

Here's the complete output of mplayer:
MPlayer 2:1.0~rc1-0ubuntu9.3 (C) 2000-2006 MPlayer Team
CPU: Genuine Intel(R) CPU           T2300  @ 1.66GHz (Family: 6, Model: 14, Stepping: 8 )
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing CIMG1096.MOV.
ISO: File Type Major Brand: Original QuickTime
Quicktime/MOV file format detected.
VIDEO:  [avc1]  1920x1080  24bpp  59.940 fps    0.0 kbps ( 0.0 kbyte/s)
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
Opening audio decoder: [imaadpcm] IMA ADPCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 177.1 kbit/12.55% (ratio: 22136->176400)
Selected audio codec: [imaadpcm] afm: imaadpcm (IMA ADPCM)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[h264 @ 0x8939638]PAFF interlacing is not implemented
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
aspect: Warning: no suitable new res found!
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 0 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
aspect: Warning: no suitable new res found!
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 1 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 2 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 3 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 4 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 5 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 6 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 7 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 8 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 9 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 10 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 11 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 12 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 13 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 14 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 15 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 16 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 17 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 18 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 19 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 20 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 21 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 22 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 23 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 24 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 25 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
[h264 @ 0x8939638]PAFF interlacing is not implemented??% ??,?% 26 0 
[h264 @ 0x8939638]concealing 4080 DC, 4080 AC, 4080 MV errors
A:   3.3 V:   0.5 A-V:  2.825 ct:  0.041  28/ 28 ??% ??% ??,?% 27 0 
Exiting... (Quit)

---

