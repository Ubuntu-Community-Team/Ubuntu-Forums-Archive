---
title: "mplayer command line and vcd"
date: 2006-12-07
forum: Multimedia &amp; Video
---

### Post by av05 on 2006-12-07
hi all,

using the mplayer gui, im able to open vcd's from the cdrom and play it correctly-
however, when running in command line 'mplayer -vo xv', i'm getting this output and nothing is played:

```
$ mplayer -vo xv vcd://
MPlayer 2:0.99+1.0pre8-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU:               Intel(R) Pentium(R) 4 CPU 3.00GHz (Family: 15, Model: 4, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


/usr/share/fonts/truetype/msttcorefonts/arial.ttf doesn't look like a font description, ignoring.
Cannot load font: /usr/share/fonts/truetype/msttcorefonts/arial.ttf
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...

Playing vcd://.
track 01:  adr=1  ctrl=4  format=2  00:02:00  mode: 5
track 02:  adr=1  ctrl=4  format=2  00:08:00  mode: 5
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
==========================================================================
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 UYVY 
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 720x480 => 720x480 Packed YUY2 
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
Audio: no sound
Starting playback...
V:   0.0   0/  0 ??% ??% ??,?% 0 0 

Exiting... (End of file) 
```

does anyone have any idea what's missing???
thanks!

---

### Post by linuchsan on 2006-12-07
You have to select the right track, like mplayer vcd://track

---

