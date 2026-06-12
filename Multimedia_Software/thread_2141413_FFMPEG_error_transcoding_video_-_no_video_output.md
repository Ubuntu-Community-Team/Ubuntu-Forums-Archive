---
title: "FFMPEG error transcoding video - no video output"
date: 2013-05-02
forum: Multimedia Software
---

### Post by LuridCinema on 2013-05-02
Howdy .. I just installed 64 bit 12.04 and installed ffmpeg w/ h.264 support per the guide listed @ [https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

When I run ffmpeg it does not take any time at all to transcode like it used to and the output file only has audio..no video.

Any help please ?

```
ffmpeg -i whatever.mov -acodec libfaac -aq 100 -vcodec libx264 -ar 48000 -crf 20 -threads 0 output.mp4

ffmpeg version git-2013-05-01-c1f2c4c Copyright (c) 2000-2013 the FFmpeg developers
  built on May  1 2013 19:40:33 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libspeex --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
  libavutil      52. 27.101 / 52. 27.101
  libavcodec     55.  6.100 / 55.  6.100
  libavformat    55.  4.100 / 55.  4.100
  libavdevice    55.  0.100 / 55.  0.100
  libavfilter     3. 62.100 /  3. 62.100
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  3.100 / 52.  3.100
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x36dfaa0] max_analyze_duration 5000000 reached at 5000000 microseconds
Guessed Channel Layout for  Input Stream #0.1 : stereo
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'whatever.mov':
  Metadata:
    major_brand     : qt  
    minor_version   : 537199360
    compatible_brands: qt ?
    creation_time   : 2013-05-02 17:17:39
  Duration: 00:00:16.80, start: 0.000000, bitrate: 999155 kb/s
    Stream #0:0(eng): Video: rawvideo (2vuy / 0x79757632), uyvy422, 1920x1080, 30 fps, 30 tbr, 30 tbn, 30 tbc
    Metadata:
      creation_time   : 2013-05-02 17:17:39
      handler_name    : Apple Alias Data Handler
    Stream #0:1(eng): Audio: pcm_s16le (sowt / 0x74776F73), 48000 Hz, stereo, s16, 1536 kb/s
    Metadata:
      creation_time   : 2013-05-02 17:17:39
      handler_name    : Apple Alias Data Handler
    Stream #0:2(eng): Data: none (tmcd / 0x64636D74)
    Metadata:
      creation_time   : 2013-05-02 17:17:39
      handler_name    : Apple Alias Data Handler
No pixel format specified, yuv422p for H.264 encoding chosen.
Use -pix_fmt yuv420p for compatibility with outdated media players.
[libx264 @ 0x36f6660] using cpu capabilities: MMX2 SSE2Fast SSSE3 SSE4.2
[libx264 @ 0x36f6660] profile High 4:2:2, level 4.0, 4:2:2 8-bit
[libx264 @ 0x36f6660] 264 - core 132 r2 76a5c3a - H.264/MPEG-4 AVC codec - Copyleft 2003-2013 - http://www.videolan.org/x264.html - options:  cabac=1 ref=3 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=7 psy=1 psy_rd=1.00:0.00 mixed_ref=1 me_range=16 chroma_me=1 trellis=1 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=1 chroma_qp_offset=-2 threads=6 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=3 b_pyramid=2 b_adapt=1 b_bias=0 direct=1 weightb=1 open_gop=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc_lookahead=40 rc=crf mbtree=1 crf=20.0 qcomp=0.60 qpmin=0 qpmax=69 qpstep=4 ip_ratio=1.40 aq=1:1.00
Output #0, mp4, to 'output.mp4':
  Metadata:
    major_brand     : qt  
    minor_version   : 537199360
    compatible_brands: qt ?
    encoder         : Lavf55.4.100
    Stream #0:0(eng): Video: h264 (libx264) ([33][0][0][0] / 0x0021), yuv422p, 1920x1080, q=-1--1, 15360 tbn, 30 tbc
    Metadata:
      creation_time   : 2013-05-02 17:17:39
      handler_name    : Apple Alias Data Handler
    Stream #0:1(eng): Audio: aac (libfaac) ([64][0][0][0] / 0x0040), 48000 Hz, stereo, s16, 128 kb/s
    Metadata:
      creation_time   : 2013-05-02 17:17:39
      handler_name    : Apple Alias Data Handler
Stream mapping:
  Stream #0:0 -> #0:0 (rawvideo -> libx264)
  Stream #0:1 -> #0:1 (pcm_s16le -> libfaac)
Press [q] to stop, [?] for help
frame=    0 fps=0.0 q=0.0 Lsize=     133kB time=00:00:16.81 bitrate=  65.0kbits/s    
video:0kB audio:130kB subtitle:0 global headers:0kB muxing overhead 2.912556%
```

---

### Post by LuridCinema on 2013-05-02
I think I figured out my issue.. I rendered the original file w/ Lightworks and I tried ffmpeg on a video that was rendered w/ Cinelerra it worked. SOOOO my issue is w/ Lightworks settings..just installed Lightworks so. time to learn !

---

### Post by LuridCinema on 2013-05-02
:guitar:  Got it figgered out..It was Lightworks ..need to play w/ the output settings. Funny the original .MOV file rendered by Lwrks played fine using VLC..however ffmpeg would not render any video.

I messed w/ some different output settings and got decent video out and was able to transcode fine w/ ffmpeg.

---

