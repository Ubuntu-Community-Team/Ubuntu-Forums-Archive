---
title: "WinFF OGV to AVI Conversion Problems In 10.04"
date: 2010-05-16
forum: Multimedia Software
---

### Post by TheFusionIcon on 2010-05-16
Oh Ubuntu, why do you torment me so? It seems like after every upgrade something important breaks. For every new feature that is added, there is also a new bug that crops up to plague my favorite OS...and now to the point.

I recently upgraded to Ubuntu 10.04 and recorded a screencast with gtk-recordMyDesktop. Upon completion of the recording I attempted to convert the OGV file to an AVI, for ease of editing purposes, using WinFF.

(And yes, I have installed libavcodec-unstripped-52) 

The result was an incredibly annoying error message Which stated:

```
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
Input #0, ogg, from '/home/thefusionicon/Desktop/out.ogv':
  Duration: 00:27:06.36, start: 0.000000, bitrate: 239 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, 1280x800, PAR 1:1 DAR 8:5, 30 tbr, 30 tbn, 30 tbc
    Stream #0.2: Audio: vorbis, 48000 Hz, mono, s16, 239 kb/s
swScaler: Unknown format is not supported as input pixel format
Cannot get resampling context
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
Input #0, ogg, from '/home/thefusionicon/Desktop/out.ogv':
  Duration: 00:27:06.36, start: 0.000000, bitrate: 239 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, 1280x800, PAR 1:1 DAR 8:5, 30 tbr, 30 tbn, 30 tbc
    Stream #0.2: Audio: vorbis, 48000 Hz, mono, s16, 239 kb/s
swScaler: Unknown format is not supported as input pixel format
Cannot get resampling context
Press Enter to Continue
```

Any help would be greatly appreciated.```

```

---

### Post by jdfoote on 2010-06-11
Did you ever figure this out? I'm seeing the same thing.

---

### Post by fearlsgroove on 2010-06-29
same issue here ... anyone see any resolution?

---

### Post by ron999 on 2010-06-29
Hi
There's a problem with ffmpeg converter.
A solution is to use mencoder instead.
See this thread here:-[http://ubuntuforums.org/showthread.php?t=1501566]("http://ubuntuforums.org/showthread.php?t=1501566")

---

### Post by FakeOutdoorsman on 2010-06-29
You could also compile a recent FFmpeg which does handle these oddball OGV files from recordMyDesktop.  FFmpeg from the Ubuntu repository (pre-Maverick Meerkat) is too old to deal with these files.  Compiling FFmpeg is not too hard to do:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by V. Wayne on 2010-06-29
Did you try to convert the file from the terminal command line?  Try this...
ffmpeg -i Your_Video.ogv -s qcif Your_new_Video.avi

---

