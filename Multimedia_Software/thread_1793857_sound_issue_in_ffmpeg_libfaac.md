---
title: "sound issue in ffmpeg libfaac"
date: 2011-06-30
forum: Multimedia Software
---

### Post by richie bee on 2011-06-30
I have got a "slipping" sound issue though -sort of breaking up trying to catch up...just a bit.

it just seems to be this .mov file and its the same in different players.

Code:
```
ffmpeg -i VID.mov -vcodec libx264 -preset fast -crf 23 -threads 0 -vf scale="720:trunc(ow/a/2)*2" -acodec libfaac -aq 100 wed4.flv
ffmpeg version 0.8, Copyright (c) 2000-2011 the FFmpeg developers
  built on Jun 29 2011 13:47:11 with gcc 4.1.2 20080704 (Red Hat 4.1.2-50)
  configuration: --prefix=/usr --libdir=/usr/lib64 --shlibdir=/usr/lib64 --mandir=/usr/share/man --incdir=/usr/include --enable-shared --enable-gpl --enable-version3 --enable-nonfree --enable-pthreads --enable-x11grab --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libfaac --enable-libmp3lame --enable-libopenjpeg --enable-libtheora --enable-libvorbis --enable-libx264 --enable-libxvid --enable-zlib --enable-swscale
  libavutil    51.  9. 1 / 51.  9. 1
  libavcodec   53.  7. 0 / 53.  7. 0
  libavformat  53.  4. 0 / 53.  4. 0
  libavdevice  53.  1. 1 / 53.  1. 1
  libavfilter   2. 23. 0 /  2. 23. 0
  libswscale    2.  0. 0 /  2.  0. 0
  libpostproc  51.  2. 0 / 51.  2. 0
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x1e151400] max_analyze_duration 5000000 reached at 5013333

Seems stream 0 codec frame rate differs from container frame rate: 5000.00 (5000/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'VID.mov':
  Metadata:
    major_brand     : qt
    minor_version   : 537199360
    compatible_brands: qt
    creation_time   : 2011-06-29 20:36:34
  Duration: 00:01:39.37, start: 0.000000, bitrate: 17989 kb/s
    Stream #0.0(eng): Video: h264 (Main), yuv420p, 1440x1080, 17672 kb/s, PAR 4:3 DAR 16:9, 25 fps, 25 tbr, 2500 tbn, 5k tbc
    Metadata:
      creation_time   : 2011-06-29 20:36:34
    Stream #0.1(eng): Audio: aac, 48000 Hz, stereo, s16, 313 kb/s
    Metadata:
      creation_time   : 2011-06-29 20:36:34
    Stream #0.2(eng): Data: tmcd / 0x64636D74
    Metadata:
      creation_time   : 2011-06-29 20:36:34
[buffer @ 0x1e1758e0] w:1440 h:1080 pixfmt:yuv420p tb:1/1000000 sar:4/3 sws_param:
[scale @ 0x1e196fa0] w:1440 h:1080 fmt:yuv420p -> w:720 h:538 fmt:yuv420p flags:0x4
[libx264 @ 0x1e158420] using SAR=4/3
[libx264 @ 0x1e158420] using cpu capabilities: MMX2 SSE2Fast SSSE3 FastShuffle SSE4.2
[libx264 @ 0x1e158420] profile High, level 3.0
[libx264 @ 0x1e158420] 264 - core 115 r2008 4c552d8 - H.264/MPEG-4 AVC codec - Copyleft 2003-2011 - http://www.videolan.org/x264.html - options: cabac=1 ref=2 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=6 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=1 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=30 rc=crf mbtree=1 crf=23.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
Output #0, flv, to 'wed4.flv':
  Metadata:
    major_brand     : qt
    minor_version   : 537199360
    compatible_brands: qt
    creation_time   : 2011-06-29 20:36:34
    encoder         : Lavf53.4.0
    Stream #0.0(eng): Video: libx264, yuv420p, 720x538 [PAR 4:3 DAR 480:269], q=2-31, 200 kb/s, 1k tbn, 25 tbc
    Metadata:
      creation_time   : 2011-06-29 20:36:34
    Stream #0.1(eng): Audio: libfaac, 48000 Hz, stereo, s16, 64 kb/s
    Metadata:
      creation_time   : 2011-06-29 20:36:34
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop, [?] for help
frame= 2484 fps= 50 q=-1.0 Lsize=   14920kB time=00:01:39.28 bitrate=1231.1kbits/s
video:12999kB audio:1795kB global headers:0kB muxing overhead 0.853988%
frame I:59    Avg QP:20.53  size: 22467
[libx264 @ 0x1e158420] frame P:1676  Avg QP:24.42  size:  6453
[libx264 @ 0x1e158420] frame B:749   Avg QP:27.24  size:  1561
[libx264 @ 0x1e158420] consecutive B-frames: 54.1% 14.7%  6.6% 24.5%
[libx264 @ 0x1e158420] mb I  I16..4: 20.2% 61.2% 18.6%
[libx264 @ 0x1e158420] mb P  I16..4:  6.8% 11.7%  2.1%  P16..4: 23.9%  9.7%  4.3%  0.0%  0.0%    skip:41.4%
[libx264 @ 0x1e158420] mb B  I16..4:  1.0%  1.9%  0.4%  B16..8: 10.6%  3.8%  0.5%  direct: 5.0%  skip:76.9%  L0:36.5% L1:49.8% BI:13.7%
[libx264 @ 0x1e158420] 8x8 transform intra:57.3% inter:72.4%
[libx264 @ 0x1e158420] coded y,uvDC,uvAC intra: 47.8% 54.1% 20.0% inter: 13.8% 13.4% 1.2%
[libx264 @ 0x1e158420] i16 v,h,dc,p: 34% 43%  4% 19%
[libx264 @ 0x1e158420] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 19% 20% 21%  5%  7%  7%  7%  6%  7%
[libx264 @ 0x1e158420] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 24% 23% 16%  5%  8%  7%  7%  5%  5%
[libx264 @ 0x1e158420] i8c dc,h,v,p: 57% 20% 16%  7%
[libx264 @ 0x1e158420] Weighted P-Frames: Y:2.0% UV:1.4%
[libx264 @ 0x1e158420] ref P L0: 83.1% 16.9%
[libx264 @ 0x1e158420] ref B L0: 88.8% 11.2%
[libx264 @ 0x1e158420] ref B L1: 97.6%  2.4%
[libx264 @ 0x1e158420] kb/s:1071.65
```

---

### Post by FakeOutdoorsman on 2011-06-30
Answered in [Re: ffmpeg to .flv quality issues](http://ubuntuforums.org/showthread.php?p=10998524#post10998524).

---

