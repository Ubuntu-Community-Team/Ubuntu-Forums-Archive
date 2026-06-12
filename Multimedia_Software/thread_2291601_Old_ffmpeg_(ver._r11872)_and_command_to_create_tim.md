---
title: "Old ffmpeg (ver. r11872) and command to create timelapse"
date: 2015-08-21
forum: Multimedia Software
---

### Post by Ondrej_Kratina on 2015-08-21
I have old ffmpeg (ver. r11872) and I need creates a timelapse video. Installing the new version is not possible, so I have to make do with what I have. For the second day of testing different commands and nothing works. That's why I write here about the bailout.

**cat timelapse/19/*.jpg | ffmpeg -f x11grab -b 500k -i - timelapse/out.flv**
> FFmpeg version r11872+debian_0.svn20080206-18+lenny3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-libfaad --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Feb 13 2011 03:56:05, gcc: 4.3.2
[x11grab @ 0xf7759ea8]device: pipe: -> display: pipe: x: 0 y: 0 width: 0 height: 0
[x11grab @ 0xf7759ea8]Could not open X display.
pipe:: I/O error occured
Usually that means that input file is truncated and/or corrupted.


OR

[B]cat timelapse/19/*.jpg | ffmpeg -f image2pipe -i - timelapse/out.flv
[/B]> FFmpeg version r11872+debian_0.svn20080206-18+lenny3, Copyright (c) 2000-2008 Fabrice Bellard, et al.  configuration: --enable-gpl --enable-libfaad --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Feb 13 2011 03:56:05, gcc: 4.3.2
Input #0, image2pipe, from 'pipe:':
  Duration: N/A, bitrate: N/A
    Stream #0.0: Video: 0x0000, 25.00 tb(r)
picture size invalid (0x0)
Cannot allocate temp picture, check pix fmt


And new command:
[B]ffmpeg -i timelapse/21/*.jpg -r 19 -vcodec libtheora timelapse/out.ogv
[/B]> FFmpeg version r11872+debian_0.svn20080206-18+lenny3, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-libfaad --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Feb 13 2011 03:56:05, gcc: 4.3.2
Input #0, image2, from 'timelapse/21/1614.jpg':
  Duration: 00:00:00.0, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: mjpeg, yuvj420p, 740x555 [PAR 1:1 DAR 4:3], 25.00 tb(r)
Unable to find a suitable output format for 'timelapse/21/1615.jpg'

---

### Post by FakeOutdoorsman on 2015-08-21
Answered at [Re: Old ffmpeg (ver. r11872) and command to create timelapse](http://ffmpeg.gusari.org/viewtopic.php?f=11&t=2285#p6622).

---

