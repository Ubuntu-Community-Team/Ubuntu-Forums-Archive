---
title: "webcam --&gt; ffmpeg  --&gt; ffserver"
date: 2010-08-17
forum: Multimedia Software
---

### Post by rawat on 2010-08-17
Hi,

I want to capture web-cam input and stream it over rtp using ffmpeg. With this i also want to use ffserver to show the live capture.

I checked my web-cam through ekiga and its working fine.

Please guide me to achieve this.


I tried below things.

**/usr/bin/ffmpeg -r 15 -s 352x288 -f video4linux2 -i /dev/video0 [http://localhost:8090/feed1.ffm](http://localhost:8090/feed1.ffm)**


FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.49. 0
  libavformat   52.31. 0 / 52.48. 0
  libavdevice   52. 1. 0 / 52. 2. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 9. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
[video4linux2 @ 0x9b3b3a0][3]Capabilities: 5000001
[video4linux2 @ 0x9b3b3a0]Cannot find a proper format for codec_id 0, pix_fmt -1.
/dev/video0: I/O error occurred
Usually that means that input file is truncated and/or corrupted.


Started ffserver ( which ran fine )

**/usr/bin/ffserver **
FFserver version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.49. 0
  libavformat   52.31. 0 / 52.48. 0
  libavdevice   52. 1. 0 / 52. 2. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 9. 0
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:39:38, gcc: 4.4.3
Tue Aug 17 17:57:34 2010 FFserver started.


**OS : Ubuntu Lucid 10.04**

---

