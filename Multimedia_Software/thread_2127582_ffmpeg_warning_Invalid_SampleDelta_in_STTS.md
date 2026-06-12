---
title: "ffmpeg warning: Invalid SampleDelta in STTS"
date: 2013-03-20
forum: Multimedia Software
---

### Post by julotte on 2013-03-20
Hello,

I run Ubuntu 10.04.

I use ffmpeg to encode video files in order to use in HTML5  video tag. My input files are .mp4 files in h264 exported from Adobe  Premiere CS5 and I want to create two output files, one in h264 - aac  with higher compression in baseline profile and one in webm VP8 -  vorbis.

For some input files, I've got this warning from ffmpeg: 

 [mov,mp4,m4a,3gp,3g2,mj2 @ 0x178f3a0] Invalid SampleDelta in STTS  -31999. 

It does not prevent me from encoding the files but I would like  to ask you what does it mean and if I should care and do something about  it.

I paste here the ffmpeg log for a webm compression:

*******
ffmpeg version N-38686-gd07de6d Copyright (c) 2000-2012 the FFmpeg developers
  built on Mar  9 2012 17:08:40 with gcc 4.4.3
   configuration: --enable-libmp3lame --enable-libxvid --enable-libvorbis  --enable-gpl --enable-libfaac --enable-libtheora --enable-zlib  --disable-shared --enable-libx264 --enable-libdirac --enable-nonfree  --enable-version3 --enable-libschroedinger --enable-avfilter  --enable-libspeex --enable-libopenjpeg --enable-libgsm --enable-postproc  --enable-pthreads --enable-libopencore-amrnb --enable-libopencore-amrwb  --enable-ffplay --enable-pthreads --prefix=/usr/local --enable-x11grab  --enable-runtime-cpudetect --enable-bzlib --enable-libdc1394  --enable-libvpx
  libavutil      51. 42.100 / 51. 42.100
  libavcodec     54. 10.100 / 54. 10.100
  libavformat    54.  2.100 / 54.  2.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 63.100 /  2. 63.100
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  7.100 /  0.  7.100
  libpostproc    52.  [0.100 / 52.  0.100]("tel:0.100%20%2F%2052.%C2%A0%200.100")
[mov,mp4,m4a,3gp,3g2,mj2 @ 0x1d153a0] Invalid SampleDelta in STTS -31999
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'inputVideo.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42mp41
    creation_time   : 2012-12-14 15:25:22
  Duration: 00:01:[31.05]("tel:31.05"), start: 0.000000, bitrate: 14312 kb/s
     Stream #0:0(eng): Video: h264 (Main) (avc1 / 0x31637661), yuv420p,  800x450 [SAR 1:1 DAR 16:9], 14005 kb/s, 25.01 fps, 25 tbr, 25k tbn, 50  tbc
    Metadata:
      creation_time   : 2012-12-14 15:25:22
      handler_name    : Mainconcept MP4 Video Media Handler
    Stream #0:1(eng): Audio: aac (mp4a / 0x6134706D), 48000 Hz, stereo, s16, 317 kb/s
    Metadata:
      creation_time   : 2012-12-14 15:25:22
      handler_name    : Mainconcept MP4 Sound Media Handler
[buffer @ 0x1d152c0] w:800 h:450 pixfmt:yuv420p tb:1/1000000 sar:1/1 sws_param:
Incompatible sample format 's16' for codec 'libvorbis', auto-selecting format 'flt'
[libvpx @ 0x1d280e0] v0.9.7-p1
[libvpx @ 0x1d280e0] --enable-pic --enable-shared --disable-install-bins --disable-install-srcs --target=x86_64-linux-gcc
Output #0, webm, to '/home/juju/videos/outputVid.webm':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42mp41
    creation_time   : 2012-12-14 15:25:22
    encoder         : Lavf54.2.100
    Stream #0:0(eng): Video: vp8, yuv420p, 800x450 [SAR 1:1 DAR 16:9], q=10-42, 300 kb/s, 1k tbn, 25 tbc
    Metadata:
      creation_time   : 2012-12-14 15:25:22
      handler_name    : Mainconcept MP4 Video Media Handler
    Stream #0:1(eng): Audio: vorbis, 48000 Hz, 1 channels, flt, 96 kb/s
    Metadata:
      creation_time   : 2012-12-14 15:25:22
      handler_name    : Mainconcept MP4 Sound Media Handler
Stream mapping:
  Stream #0:0 -> #0:0 (h264 -> libvpx)
  Stream #0:1 -> #0:1 (aac -> libvorbis)
Press [q] to stop, [?] for help
frame= 2275 fps= 11 q=0.0 Lsize=    3989kB time=00:01:[31.04]("tel:31.04") bitrate= 358.9kbits/s    
video:2870kB audio:1067kB global headers:4kB muxing overhead 1.219887%
********



Thank you very much for your advice!

---

