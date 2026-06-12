---
title: "Mplayer won't play some DVDs (Xine will)"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by abovett on 2007-04-20
Hi

I can't get Mplayer (or gmplayer) to play commercial DVDs, even though Xine will. Mplayer _will_ play an unencrypted DVD I have. With the commercial DVDs, mplayer just exits, and gmplayer just sits there and does nothing.

I'm getting the same results on a Ubuntu Feisty box and a Kubuntu Edgy box, so I'm guessing it's something I've set up or installed wrong, but I have installed all the obvious things (like libdvdcss2). As Xine plays the DVDs 

 If I run mplayer from the command line I get this:

```


[andrew@europa ~]$ mplayer dvd://1
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Duron(tm) (Family: 6, Model: 3, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 0 SSE2: 0
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvd://1.
There are 5 titles on this DVD.
There are 1 chapters in this DVD title.
There are 1 angles in this DVD title.
number of audio channels on disk: 0.
number of subtitles on disk: 0
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll
MPEG-PS file format detected.
MPEG: No audio stream found -> no sound.
VIDEO:  MPEG2  720x576  (aspect 3)  25.000 fps  8000.0 kbps (1000.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: Permission denied.
[VO_3DFX] Unable to open /dev/3dfx.
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
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 720x576 => 1024x576 Planar YV12 
V:   0.0   1/  1 ??% ??% ??,?% 0 0 

Exiting... (End of file)
[andrew@europa ~]$ 


```

Any ideas, anyone? 

Andy B

---

### Post by BigSix on 2007-09-23
I think it's sony's fault.

[http://en.wikipedia.org/wiki/ARccOS](http://en.wikipedia.org/wiki/ARccOS)

are the dvd's that don't work on this list?

---

### Post by R.Bucky on 2007-09-23
I have played many DVD's without fail using VLC media player. It is uber-lightweight and the codecs are great.

---

