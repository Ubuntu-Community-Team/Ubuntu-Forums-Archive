---
title: "avconv produces stuttering video"
date: 2012-12-06
forum: Multimedia Software
---

### Post by ericwdanielson on 2012-12-06
Hi Up till now I've been using transcoder to conver vob files to avi and it has been working great. I recently tried avconv and I like it better because it is much faster and it supports multithreading without avsync issues. The quality of the movie seems to be great with avconv except every 3-6 seconds the movie pauses during playback for the briefest of moments. It's just barely detectable but incredibly irritating. I tried using various codecs but it seems to happen for all of them. If I use transcoder on the same vob file I don't have the issue so I don't think it is the software I'm using to play it back. I suspect that I'm using avconv incorrectly but I can't figure out what I'm doing wrong.

Here is the command I'm using:
avconv -i $name.vob -c:v libx264 -preset fast -crf 18 -c:a copy -y $name.mkv

I've tried using -y $name.mp4 and $name.avi all with the same effect
I've tried chaing the frame rate, bitrate and presets but nothing seems to stop the stuttering.

If anyone has encountered such a problem or might have a suggestion to what the problem is I'd appreciate your input. Thanks in advance

---

### Post by andrew.46 on 2012-12-06
Can you give the command and complete terminal output from one fo your transcode?

---

### Post by ericwdanielson on 2012-12-07
Here is what I used for transcode (second pass)

transcode -H 10 -i $name.vob -a 0 -w 5000,50 -A -N 0x2000 -M 2 -R 2,divx4.log -o $name.avi -y xvid4,tcaud

---

### Post by ericwdanielson on 2012-12-07
eric@eric-desktop:~/Desktop/RIPDVD$ ./avconvvob
Trancoding vob to avi
Only Pass of ATHE_AMAZING_SPIDER_MAN1
avconv version 0.8.4-4:0.8.4-0ubuntu0.12.04.1, Copyright (c) 2000-2012 the Libav developers
  built on Nov  6 2012 16:50:25 with gcc 4.6.3
[mpeg @ 0x9d75220] max_analyze_duration reached
Input #0, mpeg, from 'ATHE_AMAZING_SPIDER_MAN1.vob':
  Duration: 02:16:17.92, start: 0.280633, bitrate: 5530 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x480 [PAR 32:27 DAR 16:9], 9800 kb/s, 24.10 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
    Stream #0.2[0x81]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
    Stream #0.3[0x82]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
    Stream #0.4[0x83]: Audio: ac3, 48000 Hz, 5.1, s16, 384 kb/s
[buffer @ 0x9d7cf80] w:720 h:480 pixfmt:yuv420p
[libx264 @ 0x9d75cc0] using SAR=32/27
[libx264 @ 0x9d75cc0] using cpu capabilities: MMX2 SSE2Fast FastShuffle SSEMisalign LZCNT
[libx264 @ 0x9d75cc0] profile Main, level 3.0
[libx264 @ 0x9d75cc0] 264 - core 120 r2151 a3f4407 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - [http://www.videolan.org/x264.html](http://www.videolan.org/x264.html) - options: cabac=1 ref=2 deblock=1:0:0 analyse=0x1:0x111 me=hex subme=6 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=1 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=9 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=0 b_adapt=1 b_bias=0 direct=1 weightb=0 open_gop=1 weightp=1 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=30 rc=crf mbtree=1 crf=18.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.25 aq=1:1.00
Output #0, matroska, to 'ATHE_AMAZING_SPIDER_MAN1.mkv':
  Metadata:
    encoder         : Lavf53.21.0
    Stream #0.0: Video: libx264, yuv420p, 720x480 [PAR 32:27 DAR 16:9], q=-1--1, 1k tbn, 29.97 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, 448 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (mpeg2video -> libx264)
  Stream #0:1 -> #0:1 (copy)
Press ctrl-c to stop encoding
^Cframe= 2351 fps=186 q=-1.0 Lsize=   18166kB time=97.82 bitrate=1521.2kbits/s    
video:12777kB audio:5350kB global headers:0kB muxing overhead 0.212588%
[libx264 @ 0x9d75cc0] frame I:61    Avg QP:15.65  size: 32804
[libx264 @ 0x9d75cc0] frame P:1146  Avg QP:17.59  size:  8029
[libx264 @ 0x9d75cc0] frame B:1144  Avg QP:20.48  size:  1644
[libx264 @ 0x9d75cc0] consecutive B-frames: 28.0% 17.8% 10.5% 43.7%
[libx264 @ 0x9d75cc0] mb I  I16..4: 38.8%  0.0% 61.2%
[libx264 @ 0x9d75cc0] mb P  I16..4:  9.9%  0.0%  8.6%  P16..4: 30.1% 11.6%  5.6%  0.0%  0.0%    skip:34.3%
[libx264 @ 0x9d75cc0] mb B  I16..4:  3.6%  0.0%  0.3%  B16..8: 21.1%  5.7%  0.3%  direct: 8.6%  skip:60.3%  L0:36.6% L1:51.0% BI:12.4%
[libx264 @ 0x9d75cc0] coded y,uvDC,uvAC intra: 44.4% 66.4% 35.5% inter: 11.6% 20.1% 1.8%
[libx264 @ 0x9d75cc0] i16 v,h,dc,p: 54% 21% 10% 16%
[libx264 @ 0x9d75cc0] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 20% 20% 40%  0%  0%  5%  5% 10%  0%
[libx264 @ 0x9d75cc0] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 25% 16% 23%  5%  7%  7%  6%  6%  4%
[libx264 @ 0x9d75cc0] i8c dc,h,v,p: 48% 23% 23%  6%
[libx264 @ 0x9d75cc0] Weighted P-Frames: Y:13.6% UV:7.3%
[libx264 @ 0x9d75cc0] ref P L0: 79.8% 20.2%
[libx264 @ 0x9d75cc0] kb/s:1068.05
Received signal 2: terminating.
eric@eric-desktop:~/Desktop/RIPDVD$

---

### Post by GrouchyGaijin on 2012-12-29
I don't know if this is at all related or not, but I get jerky video too when going from .mov to .flv.  See my post at:[http://ubuntuforums.org/showthread.php?t=2099383]("http://ubuntuforums.org/showthread.php?t=2099383")

---

