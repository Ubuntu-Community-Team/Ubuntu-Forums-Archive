---
title: "avconv question"
date: 2012-08-25
forum: Multimedia Software
---

### Post by marciano#1 on 2012-08-25
Hello, my knowlodgement about video is 0.0001/10
I want to convert some vob file to avi
I get these error messages
[COLOR="Blue"]avconv -i  /home/.../Videos/VTS_01_1.VOB /home/.../Videos/v1.avi
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
[mpeg @ 0x83be240] Invalid timestamps stream=0, pts=142909, dts=146509, size=2015
[mpeg @ 0x83be240] Invalid timestamps stream=0, pts=315709, dts=319309, size=2015
[mpeg @ 0x83be240] max_analyze_duration reached
Input #0, mpeg, from '/home/daniel/Videos/VTS_01_1.VOB':
  Duration: 00:17:23.37, start: 0.307878, bitrate: 5402 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x576 [PAR 64:45 DAR 16:9], 9610 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0x1c0]: Audio: mp2, 48000 Hz, stereo, s16, 384 kb/s
[buffer @ 0x83c11a0] w:720 h:576 pixfmt:yuv420p
Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'
[ac3 @ 0x83c3e40] invalid bit rate
Output #0, avi, to '/home/daniel/Videos/v1.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 720x576 [PAR 64:45 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 25 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, stereo, flt, 200 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg2video -> mpeg4)
  Stream #0:1 -> #0:1 (mp2 -> ac3)
Error while opening encoder for output stream #0:1 - maybe incorrect parameters such as bit_rate, rate, width or height
[/COLOR]

libavcodec-extra-53 is already installed

Thanks in advance for your help

---

