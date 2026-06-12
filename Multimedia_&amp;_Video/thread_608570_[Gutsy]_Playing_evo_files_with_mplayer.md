---
title: "[Gutsy] Playing evo files with mplayer"
date: 2007-11-10
forum: Multimedia &amp; Video
---

### Post by rexio8 on 2007-11-10
Hello!

I am having problems with playing a decrypted HD-DVD movie (EVO files) with mplayer. I downloaded the latest mplayer sources from svn and managed to compile them. I have video but no audio. I would be very grateful for any help to fix this matter. 
Here is the output from mplayer and ffmpeg(also from svn):
```
rex@devil:/media/dysk_d/Batman.Begins.HD-DVD.1080p.VC-1.DDPlus.5.1.EVO/HVDVD_TS$ ffmpeg -i PEVOB_1.EVO 
FFmpeg version SVN-r10970, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: 
  libavutil version: 49.5.0
  libavcodec version: 51.48.0
  libavformat version: 51.18.0
  built on Nov  9 2007 19:40:53, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mpeg, from 'PEVOB_1.EVO':
  Duration: 01:19:50.1, start: 0.038056, bitrate: 19622 kb/s
    Stream #0.0[0xfd55]: Video: vc1, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 29.97 fps(r)
    Stream #0.1[0xfd56]: Video: vc1, yuv420p, 720x480 [PAR 10:11 DAR 15:11], 29.97 fps(r)
    Stream #0.2[0xc8]: Audio: 0x0000, 48000 Hz, stereo, 192 kb/s
    Stream #0.3[0xc3]: Audio: 0x0000, 48000 Hz, 5:1, 640 kb/s
    Stream #0.4[0xc2]: Audio: 0x0000, 48000 Hz, 5:1, 640 kb/s
    Stream #0.5[0xc0]: Audio: 0x0000, 48000 Hz, 5:1, 640 kb/s
    Stream #0.6[0xb1]: Audio: 0x0000
Must supply at least one output file

```

```
rex@devil:/media/dysk_d/Batman.Begins.HD-DVD.1080p.VC-1.DDPlus.5.1.EVO/HVDVD_TS$ mplayer -vc ffvc1 PEVOB_1.EVO 
MPlayer dev-SVN-r25008-4.1.3 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 9)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2

Playing PEVOB_1.EVO.
MPEG-PS file format detected.
Searching for VC1 sequence header... found
VIDEO:  VC-1  1920x1080, 29.970 fps, header len: 36
==========================================================================
Forced video codec: ffvc1
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg M$ WVC1)
==========================================================================
==========================================================================
Opening audio decoder: [liba52] AC3 decoding with liba52
Using SSE optimized IMDCT transform

Too many video packets in the buffer: (4096 in 8274174 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A52 sync failed
ADecoder init failed :(
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders

Too many video packets in the buffer: (4096 in 8274174 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [hwac3] AC3/DTS pass-through S/PDIF
No accelerated IMDCT transform found

Too many video packets in the buffer: (4096 in 8274174 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
AC3/DTS sync failed
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x2000.
Read DOCS/HTML/en/codecs.html!
Audio: no sound
Starting playback...
VDec: vo config request - 1920 x 1080 (preferred colorspace: Planar YV12)       
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1920x1080 => 1920x1080 Planar YV12 
[ASPECT] Warning: No suitable new res found!
New_Face failed. Maybe the font path is wrong.
Please supply the text font file (~/.mplayer/subfont.ttf).
subtitle font: load_sub_face failed.
V:   8.8 211/211 136%  6%  0.0% 0 0                                             
Exiting... (Quit)

```

I believe that the problem is with the e-ac3 format. Is there some kind of codec for it available?

---

