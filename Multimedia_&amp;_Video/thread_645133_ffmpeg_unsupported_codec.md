---
title: "ffmpeg unsupported codec"
date: 2007-12-19
forum: Multimedia &amp; Video
---

### Post by j0sh78 on 2007-12-19
hi all
i'm tryng to convert an avi to 3gp

this is the output

```
$ ffmpeg -i test.avi -ar 16000 -ac 1 -acodec amr_wb -vcodec h263 -s 176x144 -r 12 -b 1000 -ab 12.2k -sameq test.3gp
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Nov 17 2007 21:23:57, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, avi, from 'test.avi':
  Duration: 01:46:07.5, start: 0.000000, bitrate: 919 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 432x240, 25.00 fps(r)
  Stream #0.1: Audio: 0x2000, 48000 Hz, 5:1, 448 kb/s
Output #0, 3gp, to 'test.3gp':
  Stream #0.0: Video: h263, yuv420p, 176x144, q=2-31, 1 kb/s, 12.00 fps(c)
  Stream #0.1: Audio: amr_wb, 16000 Hz, mono, 12 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=86020) for input stream #0.1
```

can you help me?
tnx

---

### Post by nae5 on 2007-12-27
[http://ubuntuforums.org/showthread.php?t=624470&highlight=3gp&page=3](http://ubuntuforums.org/showthread.php?t=624470&highlight=3gp&page=3)
[http://ubuntuforums.org/showthread.php?t=567016&highlight=ffmpeg](http://ubuntuforums.org/showthread.php?t=567016&highlight=ffmpeg)

take a look at these.  Basically you need to uninstall the ffmpeg you have and then enable the medibuntu repository. then use synaptic to install the ffmpeg that has the medibuntu repo in the description.  This one has aac and some other important stuff.

---

