---
title: "Mplayer: Cannot find codec for audio format 0x56444152"
date: 2007-05-22
forum: Multimedia &amp; Video
---

### Post by jiveaxe on 2007-05-22
Hi,
I have a problem with a video file downloaded from internet. I can't play it because MPlayer doesn't find a codec for the audio format 0x56444152. I looked for this on mplayer site and on page with the list of supported codec I see the format is managed by two codecs:

    * raw DV audio decoder (libdv)
    * FFmpeg DV audio decoder

I have searched my kubuntu feisty i386 for libdv.so.2 and dvaudio, finding:

/usr/lib/xine/plugins/1.1.4/xineplug_decode_dvaudio.so
/usr/lib/libdv.so.4.0.3
/usr/lib/libdv.so.4

What is the missing file/codec? This is the only movie that gives me problems, all the others play perfectly.

Thanks,
Giuseppe


P.S.
The output of mplayer:
```
gius@kubuntu-home:/TVRecords$ mplayer Smallville.621.Prototype.avi
MPlayer 2:1.0~rc1-0ubuntu9 (C) 2000-2006 MPlayer Team
CPU: AMD Athlon(tm) 64 Processor 3000+ (Family: 15, Model: 47, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing Smallville.621.Prototype.avi.
libavformat file format detected.
LAVF_header: av_open_input_stream() failed
RAWDV file format detected.
VIDEO:  [DVSD]  720x480  24bpp  29.970 fps    0.0 kbps ( 0.0 kbyte/s)
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
open: No such file or directory
[MGA] Couldn't open: /dev/mga_vid
[VO_TDFXFB] Can't open /dev/fb0: No such file or directory.
[VO_3DFX] Unable to open /dev/3dfx.
==========================================================================
Opening video decoder: [dshow] DirectShow video codecs
Decoder supports the following YUV formats: YUY2 UYVY
Decoder is capable of YUV output (flags 0x9)
VDec: vo config request - 720 x 480 (preferred colorspace: Packed YUY2)
[PP] Using codec's postprocessing, max q = 4.
Could not find matching colorspace - retrying with -vf scale...
Opening video filter: [scale]
VDec: using Packed YUY2 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 4
SwScaler: reducing / aligning filtersize 1 -> 1
SwScaler: reducing / aligning filtersize 9 -> 8

SwScaler: BICUBIC scaler, from yuyv422 to yuv420p using MMX2
SwScaler: using 4-tap MMX scaler for horizontal luminance scaling
SwScaler: using 4-tap MMX scaler for horizontal chrominance scaling
SwScaler: using 1-tap MMX "scaler" for vertical scaling (YV12 like)
SwScaler: 720x480 -> 720x480
VO: [xv] 720x480 => 720x480 Planar YV12
Selected video codec: [qdv] vfm: dshow (Sony Digital Video (DV))
==========================================================================
==========================================================================
Forced audio codec: mad
Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
```

---

### Post by shaggly on 2007-06-12
Just got the same identical error myself, so it's nice to see that someone posted here to help you out in the last 3 weeks :(

More research required then, I suppose. Strange, as I've been chugging along nicely up to now with almost all media formats.

---

### Post by dannyboy79 on 2007-06-12
well a 1 minute gogle search found this: [http://www.mplayerhq.hu/DOCS/codecs-status.html](http://www.mplayerhq.hu/DOCS/codecs-status.html)
which leads me to believe you need to install the **libdv** library. Good luck

PS (gogle should be your best friend before posting, it's the best way to learn)

---

### Post by skewray on 2007-11-30
I have this same problem.  Libdv is installed.  There must be more to the problem.

---

### Post by vrix on 2007-12-08
this might help: [http://ooboontoo.blogspot.com/]("http://ooboontoo.blogspot.com/")

---

