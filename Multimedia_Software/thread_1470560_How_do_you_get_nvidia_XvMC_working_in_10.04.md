---
title: "How do you get nvidia XvMC working in 10.04?"
date: 2010-05-02
forum: Multimedia Software
---

### Post by epi 1:10,000 on 2010-05-02
When I type in -> mplayer -fs -zoom -quiet -vo xvmc -vc ffmpeg12mc ~/Downloads/ST-TGN-G*     I get:

bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)

above mesage repeated 10 more times

MPlayer SVN-r1.0~rc3+svn20090426-4.4.3 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/rgwa/Downloads/ST-TGN-Gambit.mpg..mpg.
TS file format detected.
VIDEO MPEG2(pid=2368) AUDIO A52(pid=2369) NO SUBS (yet)!  PROGRAM N. 1
VIDEO:  MPEG2  704x480  (aspect 2)  29.970 fps  4393.6 kbps (549.2 kbyte/s)
vo_xvmc: X-Video extension 2.2
vo_xvmc: X-Video MotionCompensation Extension version 1.1
==========================================================================
Forced video codec: ffmpeg12mc
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
[VD_FFMPEG] XVMC accelerated codec.
[VD_FFMPEG] XVMC-accelerated MPEG-2.
[VD_FFMPEG] XVMC-accelerated MPEG-2.
Selected video codec: [ffmpeg12mc] vfm: ffmpeg (FFmpeg MPEG-1/2 (XvMC))
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform
Using MMX optimized resampler
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [a52] afm: liba52 (AC3-liba52)
==========================================================================
AO: [pulse] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
[VD_FFMPEG] Trying pixfmt=0.
[VD_FFMPEG] XVMC-accelerated MPEG-2.
VDec: vo config request - 704 x 480 (preferred colorspace: MPEG1/2 Motion Compensation and IDCT)
vo_xvmc: Found matching surface with id=54434449 on 361 port at 0 adapter
VDec: using MPEG1/2 Motion Compensation and IDCT as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xvmc] 704x480 => 704x528 MPEG1/2 Motion Compensation and IDCT  [fs] [zoom]
vo_xvmc: Found matching surface with id=54434449 on 361 port at 0 adapter
vo_xvmc: Using Xv Adaptor #0 (NV17 Video Texture)
vo_xvmc: Port 361 grabed
/usr/lib/libXvMC.so.1: undefined symbol: XvMCCreateContext
vo_xvmc: XvMCCreateContext failed with error 2
FATAL: Cannot initialize video driver.
[VD_FFMPEG] Trying pixfmt=1.
[VD_FFMPEG] XVMC-accelerated MPEG-2.
VDec: vo config request - 704 x 480 (preferred colorspace: MPEG1/2 Motion Compensation)
vo_xvmc: Found matching surface with id=54434449 on 361 port at 0 adapter
VDec: using MPEG1/2 Motion Compensation and IDCT as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xvmc] 704x480 => 704x528 MPEG1/2 Motion Compensation and IDCT  [fs] [zoom]
vo_xvmc: Found matching surface with id=54434449 on 361 port at 0 adapter
vo_xvmc: Using Xv Adaptor #0 (NV17 Video Texture)
vo_xvmc: Port 361 grabed
vo_xvmc: XvMCCreateContext failed with error 2
FATAL: Cannot initialize video driver.
Unsupported PixelFormat -1
[mpegvideo_xvmc @ 0x239fac0]decoding to PIX_FMT_NONE is not supported.

FATAL: Could not initialize video filters (-vf) or video output (-vo).


Exiting... (End of file)




Originaly it said it couldn't find /etc/XvMCConfig so I created 1 with the text "libXvMC.so.1" and "libXvMCNVIDIA_dynamic.so.1"  without thee quotes in it.   

Does someone know how to configure Ubuntu 10.04 - i386 for XvMC playback?

The system is a:
P4 3GHz w/ HT
Asus P4C800-E Deluxe MoBo
EVGA e-GeForce 6600GT 128MB GDDR3
Nvidia driver 173.14.22
Ubuntu 10.04-386

---

### Post by epi 1:10,000 on 2010-05-03
Never mind I got it working w/ the tutorial @ [http://www.mythtv.org/wiki/XvMC](http://www.mythtv.org/wiki/XvMC).  Now I just need to get the sound output to work.

Im still getting bt_audio_service_open: connect() failed: Connection refused (111) and no sound output

-edit
Doh forgot to use  the 9 and 0 keys to adjust the sound (default is sound turned all the way down).

So I get my post is utterly useless.

---

### Post by epi 1:10,000 on 2010-05-05
Using bobdient causes the video and audio to drift out of sync in when exicuting mplayer in the Bash CL, as seen below:
mplayer -fs -zoom -vo xvmc:bobdeint -vc ffmpeg12mc /path/to/file

Audio and video stay in sync in MythTv .23.

What is different about mythtv's implementation of xvmc?


Edit:  adding -framedrop before the -vo comand fixes the audio sync problems

example mplayer -fs -framedrop -vo xvmc:bobdeint:queue -vc ffmpeg12mc /path/to/file

---

