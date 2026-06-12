---
title: "avconv ntsc vob"
date: 2013-09-23
forum: Multimedia Software
---

### Post by mellow5 on 2013-09-23
Hi have a vob file from an dvd recorded in ntsc. I want to convert this vob to a mp4 file with avconv. After the conversion the output file does not play as expected the pictures jump. I'm sure it's not my hardware because more demanding videos play without problems

```

avconv -i VTS_01_1.VOB  -c:v libx264  -vb 1200k -c:a libmp3lame -ab 192k -ac 2 01.mp4

```

```

avconv version 0.8.6-6:0.8.6-1ubuntu2, Copyright (c) 2000-2013 the Libav developers
  built on Mar 30 2013 22:20:06 with gcc 4.7.2
[mpeg @ 0x2113d40] max_analyze_duration reached
Input #0, mpeg, from 'VTS_01_1.VOB':
  Duration: 00:07:36.68, start: 0.045500, bitrate: 18809 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x480 [PAR 32:27 DAR 16:9], 7500 kb/s, 24.18 fps, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.2[0x81]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.3[0x2d]: Subtitle: dvdsub
    Stream #0.4[0x2c]: Subtitle: dvdsub
    Stream #0.5[0x2b]: Subtitle: dvdsub
    Stream #0.6[0x29]: Subtitle: dvdsub
    Stream #0.7[0x28]: Subtitle: dvdsub
    Stream #0.8[0x2a]: Subtitle: dvdsub
    Stream #0.9[0x27]: Subtitle: dvdsub
    Stream #0.10[0x26]: Subtitle: dvdsub
    Stream #0.11[0x25]: Subtitle: dvdsub
    Stream #0.12[0x21]: Subtitle: dvdsub
    Stream #0.13[0x20]: Subtitle: dvdsub
    Stream #0.14[0x24]: Subtitle: dvdsub
    Stream #0.15[0x23]: Subtitle: dvdsub
    Stream #0.16[0x22]: Subtitle: dvdsub
File '01.mp4' already exists. Overwrite ? [y/N] y
[buffer @ 0x223adc0] w:720 h:480 pixfmt:yuv420p
[libx264 @ 0x2116500] using SAR=32/27
[libx264 @ 0x2116500] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2 AVX
[libx264 @ 0x2116500] profile Main, level 3.1
[libx264 @ 0x2116500] 264 - core 123 r2189 35cf912 - H.264/MPEG-4 AVC codec - Copyleft 2003-2012 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x1:0x111 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=1 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=12 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=0 b_adapt=1 b_bias=0 direct=1 weightb=0 open_gop=1 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=abr mbtree=1 bitrate=1200 ratetol=1.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=1:1.00
Output #0, mp4, to '01.mp4':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: libx264, yuv420p, 720x480 [PAR 32:27 DAR 16:9], q=-1--1, 1200 kb/s, 60k tbn, 59.94 tbc
    Stream #0.1: Audio: libmp3lame, 48000 Hz, 2 channels, s16, 192 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg2video -> libx264)
  Stream #0:1 -> #0:1 (ac3 -> libmp3lame)
Press ctrl-c to stop encoding
Input stream #0:1 frame changed from rate:48000 fmt:s16 ch:6 to rate:48000 fmt:s16 ch:2

```

Any suggestions?

---

### Post by andrew.46 on 2013-09-26
Perhaps experiment with a preset:

[https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide](https://ffmpeg.org/trac/ffmpeg/wiki/x264EncodingGuide)

Not sure how well FFmpeg options map to avconv but probably you will be ok... I suspect you will need the preset + crf option on this page.

---

### Post by qyot27 on 2013-09-26
My money's on this being a multiangular video stream; having frames jerk back and forth - especially in a predictable pattern every X seconds - is the telltale sign of that.  Concert DVDs will sometimes make use of the multiple angles feature for different cameras, as do some releases for anime that store the regular and textless openings/endings in the same video stream rather than putting the textless versions in the Special Features area in a separate Title.

On a normal DVD player this would be invisible to the end user because they know how to properly parse the angles and only display the one you want to see at the time.

In the case of multiple angles, the only solution is to re-rip it and tell the ripping software to only take one of the angles.

---

### Post by qyot27 on 2013-09-27
Yeah, now after looking at that readout again, I'm 100% certain it's multiple angles.  Look at the bitrate values: the total file bitrate is 18809 kbps, but the video stream is 7500 kbps.  The audio and subs don't make up for that discrepancy, the only sane reason as to why the file bitrate is much higher is that the video stream is multiangular - two video streams at 7500 kbps put the value much closer to striking distance of 18809 kbps, when you account for the audio and subs and container overhead.

As a better explanation, multi-angle DVDs are not like having multiple video streams in a container like Matroska.  In MKV, multiple video streams are discrete and demarcated on the container level.  On a DVD, the angles are in the same stream, interleaved every half a second or so.  So if there isn't proper handling of the angle information, it looks like a single stream to the transcoding software and you'll end up with the video jerking back and forth between angles whenever they occur.

The easiest solution is as I mentioned before: in the ripping software, tell it to only rip one of the angles at a time.

As an alternative, you could try using one of the members of the mplayer family, since they do have the capability of switching between angles on DVD with the -dvdangle option (otherwise, you'd need to have the DVD structure information to give them - meaning, the .IFO files that go with the .VOB files).  mplayer and mplayer2 will only be suitable for this if you pipe yuv4mpeg out of them and give that as input to ffmpeg or avconv.  Otherwise, you'll need to use mencoder to do it, or better yet, mpv.

The reason this cannot be done with ffmpeg or avconv directly is because they don't support libdvdread and/or libdvdnav (ffmpeg does have support for libbluray, so it might handle angles on there*, but that's not helpful in this case).

*but I wouldn't know; I've not had any need thus far to test libbluray beyond compiling it, and even if I did test it there's no guarantee I have any multi-angular Blu-ray discs to test that feature with.

---

### Post by mellow5 on 2013-10-31
Finally I used dvdbackup to copy the dvd to the hard drive. Afterwards I used dvdrip to convert it. It worked. I guess the failure happened previously during the copy from disc to hard drive.

Thank you

---

