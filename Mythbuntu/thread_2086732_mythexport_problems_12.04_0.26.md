---
title: "mythexport problems 12.04 0.26"
date: 2012-11-21
forum: Mythbuntu
---

### Post by s_g_robertson on 2012-11-21
I'm having problems getting mythexport working.  It used to but it's been a while.

I'm using Mythexport package 2.2.4-0ubuntu1 with the 1.2 version of PortableH264HighRes from [http://www.baablogic.net/mythexport/](http://www.baablogic.net/mythexport/)

It's not working when used normally so trying the configuration from the file manually  I get the following:

Any thoughts?

Cheers
Stephen

avconv -i /media/disk/Recordings/1005_20120925072800.mpg -y -pass 1 -an -vcodec libx264 -pre:v libx264-medium_firstpass -pre:v libx264-ipod640 -b 1500k -bt 1000k -threads 0 -s 800x480 -aspect 16:9 -f ipod /dev/null && avconv -i /media/disk/Recordings/1005_20120925072800.mpg -y -pass 2 -vcodec libx264 -preset medium -pre:v libx264-ipod640 -b 1500k -bt 1000k -threads 0 -s 800x480 -acodec libfaac -ab 192k -ar 48000 -ac 2 -aspect 16:9 -f ipod /var/lib/mythtv
avconv version 0.8.3-4:0.8.3-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Jun 12 2012 16:37:58 with gcc 4.6.3
[mpegts @ 0x8fe6260] Continuity check failed for pid 289 expected 6 got 10
[mpegts @ 0x8fe6260] Continuity check failed for pid 0 expected 5 got 9
[mpegts @ 0x8fe6260] max_analyze_duration reached
[NULL @ 0x9003340] start time is not set in estimate_timings_from_pts
[NULL @ 0x90051c0] start time is not set in estimate_timings_from_pts
[NULL @ 0x90070e0] start time is not set in estimate_timings_from_pts
[mpegts @ 0x8fe6260] PES packet size mismatch
    Last message repeated 1 times
Input #0, mpegts, from '/media/disk/Recordings/1005_20120925072800.mpg':
  Duration: 00:13:55.42, start: 46845.884289, bitrate: 2782 kb/s
  Program 1 
    Stream #0.0[0xb86]: Video: mpeg2video (Main), yuv420p, 704x576 [PAR 16:11 DAR 16:9], 15000 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
    Stream #0.1[0xb23](eng): Audio: mp2, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.2[0xb25](eng): Audio: mp2, 48000 Hz, mono, s16, 64 kb/s (visual impaired)
    Stream #0.3[0xb24](eng): Subtitle: dvbsub
    Stream #0.4[0x856]: Data: [11][0][0][0] / 0x000B
    Stream #0.5[0x91b]: Data: [11][0][0][0] / 0x000B
    Stream #0.6[0x91c]: Data: [11][0][0][0] / 0x000B
[buffer @ 0x8fe8ca0] w:704 h:576 pixfmt:yuv420p
[scale @ 0x8fec780] w:704 h:576 fmt:yuv420p -> w:800 h:480 fmt:yuv420p flags:0x4
[libx264 @ 0x8fe94c0] using SAR=16/15
[libx264 @ 0x8fe94c0] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.1 Cache64
[libx264 @ 0x8fe94c0] ratecontrol_init: can't open stats file
Output #0, ipod, to '/dev/null':
    Stream #0.0: Video: libx264, yuv420p, 800x480 [PAR 16:15 DAR 16:9], q=-1--1, pass 1, 1500 kb/s, 90k tbn, 25 tbc
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg2video -> libx264)
Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height

---

