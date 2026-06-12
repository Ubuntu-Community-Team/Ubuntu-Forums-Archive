---
title: "mplayer dvb problem"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by gastar on 2007-11-27
Hi,

ok i am trying to setup a Multimedia Box but DVB-C is giving me a hard time (again).

My System:

Ubuntu 7.10 AMD64
DVB-C Card: Terratec Cinergy 1200 
GFX-Card: ATI x1650

The first problem i face is to get mplayer to use the dvb device (_repeatable_) without crashing.

 I can start mplayer and it will playback the TV programm (choppy but this will be the next problem ;) )  when i close mplayer and try to start it a second time it wont start again :( The only thing i can do is to restart the system. It looks like the device was killed when myplayer shuts down but is this a mplayer or driver issue ?

Has anybody a hint for me ?

Here a snapshot from my terminal:
```

/usr/src$ mplayer dvb://ZDF
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://ZDF.
dvb_tune Freq: 394000000
TS file format detected.
VIDEO MPEG2(pid=110) AUDIO MPA(pid=120) NO SUBS (yet)!  PROGRAM N. 0
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  15000.0 kbps (1875.0 kbyte/s)
xscreensaver_disable: Could not find XScreenSaver window.
gnome_screensaver_control()==========================================================================
Opening video decoder: [mpegpes] MPEG 1/2 Video passthrough
VDec: vo config request - 720 x 576 (preferred colorspace: Mpeg PES)
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
The selected video_out device is incompatible with this codec.
Try appending the scale filter to your filter list,
e.g. -vf spp,scale instead of -vf spp.
VDecoder init failed :(
Opening video decoder: [libmpeg2] MPEG 1/2 Video decoder libmpeg2-v0.4.0b
Selected video codec: [mpeg12] vfm: libmpeg2 (MPEG-1 or 2 (libmpeg2))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libmad] libmad mpeg audio decoder
AUDIO: 48000 Hz, 2 ch, s16le, 256.0 kbit/16.67% (ratio: 32000->192000)
Selected audio codec: [mad] afm: libmad (libMAD MPEG layer 1-2-3)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
VDec: vo config request - 720 x 576 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12
gnome_screensaver_control()04 ct: -0.389 713/713 14%  1% 26.3% 2 0
Exiting... (Quit)
gastar@gandalf:/usr/src$ mplayer dvb://ZDF
MPlayer 1.0rc2-4.1.3 (C) 2000-2007 MPlayer Team
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ (Family: 15, Model: 43, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://ZDF.
ERROR OPENING FRONTEND DEVICE /dev/dvb/adapter0/frontend0: ERRNO 16
DVB_SET_CHANNEL2, COULDN'T OPEN DEVICES OF CARD: 0, EXIT
ERROR, COULDN'T SET CHANNEL  126: Failed to open dvb://ZDF.
Select error: Bad file descriptor


Exiting... (End of file)

```

---

### Post by g00f on 2008-07-15
I have exactly the same problem.

I believe it is mplayer not releasing the DVB device when it closes. I can use me-tv repeatedly no problem, I can run "mplayer dvb://..." once, but next time I run mplayer I get the same message. me-tv no longer runs either.

I tried to "rmmod -f saa7134_dvb" but it says the resource in is use.

Maybe it's related to AMD or 64 bit as my other PC running Intel 32 bit doesn't have this issue.

My CPU: "AMD Athlon(tm) 64 X2 Dual Core Processor 6000+"
OS: kubuntu AMD64

---

