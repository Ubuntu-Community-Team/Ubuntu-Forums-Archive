---
title: "ffmpeg w/ x264 ignores video bitrate"
date: 2012-11-27
forum: Multimedia Software
---

### Post by Luca Borrione on 2012-11-27
Hello,

I'm using a two passes code:

**pass 1:**
```
nice ffmpeg -i input.mpeg -f matroska -map 0:0 -codec:v libx264 -profile:v high -preset:v medium -b:v 1200k -maxrate:v 1200k -bufsize:v 2400k -s:v 640x360 -aspect:v 640:360 -threads:v 0 -an -pass 1 -passlogfile "logfile" -y /dev/null
```

console output:
```
ffmpeg version git-2012-09-29-74bd0cf Copyright (c) 2000-2012 the FFmpeg developers
 built on Sep 29 2012 14:52:32 with gcc 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3)
 configuration: --enable-gpl --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
 libavutil      51. 73.101 / 51. 73.101
 libavcodec     54. 61.100 / 54. 61.100
 libavformat    54. 29.105 / 54. 29.105
 libavdevice    54.  3.100 / 54.  3.100
 libavfilter     3. 18.100 /  3. 18.100
 libswscale      2.  1.101 /  2.  1.101
 libswresample   0. 16.100 /  0. 16.100
 libpostproc    52.  1.100 / 52.  1.100
[mpeg @ 0xa1fc540] max_analyze_duration 5000000 reached at 5000000
Input #0, mpeg, from 'input.mpeg':
 Duration: 26:30:43.71, start: 0.287267, bitrate: 95 kb/s
 Stream #0:0[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x576 [SAR 64:45 DAR 16:9], 9800 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
 Stream #0:1[0x80]: Audio: ac3, 48000 Hz, 5.1(side), s16, 384 kb/s
 Stream #0:2[0x81]: Audio: ac3, 48000 Hz, 5.1(side), s16, 384 kb/s
 Stream #0:3[0x82]: Audio: ac3, 48000 Hz, 5.1(side), s16, 384 kb/s
 Stream #0:4[0x83]: Audio: ac3, 48000 Hz, mono, s16, 96 kb/s
[libx264 @ 0xa204460] using SAR=1/1
[libx264 @ 0xa204460] using cpu capabilities: MMX2 SSE2Slow SlowCTZ
[libx264 @ 0xa204460] profile Main, level 3.0
[libx264 @ 0xa204460] 264 - core 128 r2 198a7ea - H.264/MPEG-4 AVC codec - Copyleft 2003-2012 - http://www.videolan.org/x264.html - options: cabac=1 ref=1 deblock=1:0:0 analyse=0x1:0 me=dia subme=2 psy=1 psy_rd=1.00:0.00 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=0 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=0 threads=3 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=cbr mbtree=1 bitrate=1200 ratetol=1.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 vbv_maxrate=1200 vbv_bufsize=2400 nal_hrd=none ip_ratio=1.40 aq=1:1.00
Output #0, matroska, to '/dev/null':
 Metadata:
  encoder         : Lavf54.29.105
  Stream #0:0: Video: h264, yuv420p, 640x360 [SAR 1:1 DAR 16:9], q=-1--1, pass 1, 1200 kb/s, 1k tbn, 25 tbc
Stream mapping:
 Stream #0:0 -> #0:0 (mpeg2video -> libx264)
Press [q] to stop, [?] for help
frame=   61 fps=0.0 q=2.0 size=       0kB time=00:00:00.48 bitrate=   0.0kbits/
...
frame=62326 fps= 67 q=0.0 Lsize=       0kB time=00:41:32.96 bitrate=   0.0kbits/s    
video:347830kB audio:0kB subtitle:0 global headers:0kB muxing overhead -100.000000%
[libx264 @ 0xa6b6460] frame I:1037  Avg QP:15.75  size: 22859
[libx264 @ 0xa6b6460] frame P:32210 Avg QP:18.79  size:  8037
[libx264 @ 0xa6b6460] frame B:29079 Avg QP:19.30  size:  2531
[libx264 @ 0xa6b6460] consecutive B-frames: 23.6% 37.1% 16.8% 22.6%
[libx264 @ 0xa6b6460] mb I  I16..4: 30.2%  0.0% 69.8%
[libx264 @ 0xa6b6460] mb P  I16..4: 27.4%  0.0%  0.0%  P16..4: 64.7%  0.0%  0.0%  0.0%  0.0%    skip: 7.8%
[libx264 @ 0xa6b6460] mb B  I16..4:  3.5%  0.0%  0.0%  B16..8: 36.5%  0.0%  0.0%  direct:17.1%  skip:42.9%  L0:29.1% L1:45.3% BI:25.6%
[libx264 @ 0xa6b6460] coded y,uvDC,uvAC intra: 47.1% 68.6% 33.9% inter: 28.8% 28.2% 1.9%
[libx264 @ 0xa6b6460] i16 v,h,dc,p: 38% 27% 24% 11%
[libx264 @ 0xa6b6460] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 23% 21% 18%  3%  9%  6%  6%  6%  7%
[libx264 @ 0xa6b6460] i8c dc,h,v,p: 51% 22% 21%  6%
[libx264 @ 0xa6b6460] Weighted P-Frames: Y:6.9% UV:3.7%
[libx264 @ 0xa6b6460] kb/s:1142.95
```

**pass 2:**
```
nice ffmpeg -i input.mpeg -f matroska -map 0:0 -codec:v libx264 -profile:v high -preset:v medium -r:v 25 -b:v 1200k -maxrate:v 1200k -bufsize:v 2400k -s:v 640x360 -aspect:v 640:360 -threads:v 0 -codec:a libvorbis -ar:a 48000 -map 0:1 -ac:a:0 6 -b:a:0 192k -map 0:2 -ac:a:1 6 -b:a:1 192k -map 0:4 -ac:a:2 2 -b:a:2 96k -async 1 -metadata title="Title" -pass 2 -passlogfile "logfile" "output.mkv"
```

console output:
```
ffmpeg version git-2012-09-29-74bd0cf Copyright (c) 2000-2012 the FFmpeg developers
 built on Sep 29 2012 14:52:32 with gcc 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3)
 configuration: --enable-gpl --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
 libavutil      51. 73.101 / 51. 73.101
 libavcodec     54. 61.100 / 54. 61.100
 libavformat    54. 29.105 / 54. 29.105
 libavdevice    54.  3.100 / 54.  3.100
 libavfilter     3. 18.100 /  3. 18.100
 libswscale      2.  1.101 /  2.  1.101
 libswresample   0. 16.100 /  0. 16.100
 libpostproc    52.  1.100 / 52.  1.100
[mpeg @ 0x9890540] max_analyze_duration 5000000 reached at 5000000
Input #0, mpeg, from 'input.mpeg':
 Duration: 26:30:43.71, start: 0.287267, bitrate: 95 kb/s
  Stream #0:0[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x576 [SAR 64:45 DAR 16:9], 9800 kb/s, 25 fps, 25 tbr, 90k tbn, 50 tbc
  Stream #0:1[0x80]: Audio: ac3, 48000 Hz, 5.1(side), s16, 384 kb/s
  Stream #0:2[0x81]: Audio: ac3, 48000 Hz, 5.1(side), s16, 384 kb/s
  Stream #0:3[0x82]: Audio: ac3, 48000 Hz, 5.1(side), s16, 384 kb/s
  Stream #0:4[0x83]: Audio: ac3, 48000 Hz, mono, s16, 96 kb/s
 -async is forwarded to lavfi similarly to -af aresample=min_comp=0.001:min_hard_comp=0.100000.
 Last message repeated 2 times
[libx264 @ 0x9a20ba0] using SAR=1/1
[libx264 @ 0x9a20ba0] using cpu capabilities: MMX2 SSE2Slow SlowCTZ
[libx264 @ 0x9a20ba0] target: 1200.00 kbit/s, expected: 1148.59 kbit/s, avg QP: 23.3019
[libx264 @ 0x9a20ba0] profile High, level 3.0
[libx264 @ 0x9a20ba0] x264 - core 128 r2 198a7ea - H.264/MPEG-4 AVC codec - Copyleft 2003-2012 - http://www.videolan.org/x264.html - options: cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=3 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=2pass mbtree=1 bitrate=1200 ratetol=1.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 cplxblur=20.0 qblur=0.5 vbv_maxrate=1200 vbv_bufsize=2400 nal_hrd=none ip_ratio=1.40 aq=1:1.00
Output #0, matroska, to 'output.mkv':
 Metadata:
  title           : Title
  encoder         : Lavf54.29.105
  Stream #0:0: Video: h264, yuv420p, 640x360 [SAR 1:1 DAR 16:9], q=-1--1, pass 2, 1200 kb/s, 1k tbn, 25 tbc
  Stream #0:1: Audio: vorbis, 48000 Hz, 5.1, flt, 192 kb/s
  Stream #0:2: Audio: vorbis, 48000 Hz, 5.1, flt, 192 kb/s
  Stream #0:3: Audio: vorbis, 48000 Hz, stereo, flt, 96 kb/s
Stream mapping:
 Stream #0:0 -> #0:0 (mpeg2video -> libx264)
 Stream #0:1 -> #0:1 (ac3 -> libvorbis)
 Stream #0:2 -> #0:2 (ac3 -> libvorbis)
 Stream #0:4 -> #0:3 (ac3 -> libvorbis)
Press [q] to stop, [?] for help
[libvorbis @ 0x9a215c0] Que input is backward in time
[libvorbis @ 0x993b480] Que input is backward in time
[libvorbis @ 0x99dd580] Que input is backward in time
frame=   23 fps=0.0 q=17.0 size=      17kB time=00:00:00.60 bitrate= 237.8kbits
...
frame=62326 fps= 14 q=12.0 Lsize=  468644kB time=00:41:32.96 bitrate=1540.0kbits/s    
video:349160kB audio:115907kB subtitle:0 global headers:17kB muxing overhead 0.765580%
[libx264 @ 0xa645ba0] frame I:1037  Avg QP:16.95  size: 19321
[libx264 @ 0xa645ba0] frame P:32210 Avg QP:19.35  size:  8075
[libx264 @ 0xa645ba0] frame B:29079 Avg QP:20.61  size:  2662
[libx264 @ 0xa645ba0] consecutive B-frames: 23.6% 37.1% 16.8% 22.6%
[libx264 @ 0xa645ba0] mb I  I16..4: 12.0% 69.9% 18.0%
[libx264 @ 0xa645ba0] mb P  I16..4:  3.3% 11.3%  1.7%  P16..4: 41.2% 23.5% 10.6%  0.0%  0.0%    skip: 8.2%
[libx264 @ 0xa645ba0] mb B  I16..4:  0.2%  0.5%  0.1%  B16..8: 42.6% 10.0%  2.0%  direct: 5.0%  skip:39.7%  L0:36.7% L1:50.7% BI:12.6%
[libx264 @ 0xa645ba0] 8x8 transform intra:69.0% inter:69.8%
[libx264 @ 0xa645ba0] coded y,uvDC,uvAC intra: 64.4% 81.6% 50.6% inter: 32.1% 37.3% 4.0%
[libx264 @ 0xa645ba0] i16 v,h,dc,p: 35% 22%  8% 36%
[libx264 @ 0xa645ba0] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 18% 15% 23%  5%  8%  9%  8%  7%  7%
[libx264 @ 0xa645ba0] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 22% 21% 18%  5%  9%  8%  7%  5%  5%
[libx264 @ 0xa645ba0] i8c dc,h,v,p: 52% 21% 19%  8%
[libx264 @ 0xa645ba0] Weighted P-Frames: Y:7.5% UV:3.7%
[libx264 @ 0xa645ba0] ref P L0: 63.1% 14.4% 15.3%  6.6%  0.6%
[libx264 @ 0xa645ba0] ref B L0: 87.0% 12.0%  1.1%
[libx264 @ 0xa645ba0] ref B L1: 95.8%  4.2%
[libx264 @ 0xa645ba0] kb/s:1147.32
```

After that I run:
```
ffmpeg -i output.mkv
```
output:
```
ffmpeg version git-2012-09-29-74bd0cf Copyright (c) 2000-2012 the FFmpeg developers
 built on Sep 29 2012 14:52:32 with gcc 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3)
 configuration: --enable-gpl --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
 libavutil      51. 73.101 / 51. 73.101
 libavcodec     54. 61.100 / 54. 61.100
 libavformat    54. 29.105 / 54. 29.105
 libavdevice    54.  3.100 / 54.  3.100
 libavfilter     3. 18.100 /  3. 18.100
 libswscale      2.  1.101 /  2.  1.101
 libswresample   0. 16.100 /  0. 16.100
 libpostproc    52.  1.100 / 52.  1.100
Input #0, matroska,webm, from 'output.mkv':
 Metadata:
  title           : Title
  ENCODER         : Lavf54.29.105
 Duration: 00:41:33.04, start: 0.000000, bitrate: 1539 kb/s
  Stream #0:0: Video: h264 (High), yuv420p, 640x360 [SAR 1:1 DAR 16:9], 25 fps, 25 tbr, 1k tbn, 50 tbc (default)
  Stream #0:1: Audio: vorbis, 48000 Hz, 5.1, s16 (default)
  Stream #0:2: Audio: vorbis, 48000 Hz, 5.1, s16 (default)
  Stream #0:3: Audio: vorbis, 48000 Hz, stereo, s16 (default)
```

[B][COLOR="Blue"]Why does my video has a bitrate of 1539 while I specified it to be 1200?
And how can I obtain it to be 1200 as wanted?[/COLOR][/B]

---

### Post by Luca Borrione on 2012-11-27
Ok guys: I used [mediainfo]("http://mediainfo.sourceforge.net/") to get more info  on my video file and noticed that the bitrate of 1539 is an overall bitrate

1539 (overall) - 192 (first audio) - 192 (second audio) - 96 (third audio) = 1059 kbps (video bitrate)

Mediainfo gives me 1029 kbps for the audio, while reporting the nominal bitrate of 1200.

So my code is right.
Thank you

---

### Post by evilsoup on 2012-11-27
That bit rate is the combined bit rates of all the streams (video+3 audio). My version of ffmpeg/avconv lists the bit rates of individual streams as well, I'm not sure why yours doesn't.

---

### Post by Luca Borrione on 2012-11-28
@evilsoup

Thank you to confirm this.

Cheers!

---

