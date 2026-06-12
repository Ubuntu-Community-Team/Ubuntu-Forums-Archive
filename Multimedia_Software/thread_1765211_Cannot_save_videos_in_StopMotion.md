---
title: "Cannot save videos in StopMotion"
date: 2011-05-22
forum: Multimedia Software
---

### Post by Webster12 on 2011-05-22
Hi,

Please help. I am getting an error whenever I try to save in stopmotion. The is:

>  p, li { white-space: pre-wrap; } FFmpeg version 0.6-4:0.6-2ubuntu6.1, Copyright (c) 2000-2010 the FFmpeg developers
   built on Mar 31 2011 18:42:12 with gcc 4.4.5
   configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
   WARNING: library configuration mismatch
   libavutil   configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
   libavcodec  configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
   libavformat configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
   libavdevice configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
   libavfilter configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
   libswscale  configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
   libpostproc configuration: --extra-version=4:0.6-2ubuntu6.1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
   libavutil     50.15. 1 / 50.15. 1
   libavcodec    52.72. 2 / 52.72. 2
   libavformat   52.64. 2 / 52.64. 2
   libavdevice   52. 2. 0 / 52. 2. 0
   libavfilter    1.19. 0 /  1.19. 0
   libswscale     0.11. 0 /  0.11. 0
   libpostproc   51. 2. 0 / 51. 2. 0
 Input #0, image2, from '/home/japi/.stopmotion/packer/stopmotion.gif/images/%06d.jpg':
   Duration: 00:00:00.80, start: 0.000000, bitrate: N/A
     Stream #0.0: Video: mjpeg, yuvj420p, 640x480 [PAR 1:1 DAR 4:3], 10 fps, 10 tbr, 10 tbn, 10 tbc
 [mpeg1video @ 0x87cb680]MPEG1/2 does not support 10/1 fps
 Output #0, mpeg, to '/home/japi/Videos/stopmotion.mpeg':
     Stream #0.0: Video: mpeg1video, yuv420p, 640x480 [PAR 1:1 DAR 4:3], q=2-31, 1 kb/s, 90k tbn, 10 tbc
 Stream mapping:
   Stream #0.0 -> #0.0
 Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
 

Thanks!

---

