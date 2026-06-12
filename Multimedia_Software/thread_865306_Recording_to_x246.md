---
title: "Recording to x246"
date: 2008-07-20
forum: Multimedia Software
---

### Post by mikeym on 2008-07-20
Hi,

I was trying to use a script I found for converting to x246 using ffmpeg and I'm getting a problem.

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:22:28, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mpeg, from 'title1.vob':
  Duration: 02:18:24.7, start: 0.049756, bitrate: 5645 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 9800 kb/s, 25.00 fps(r)
  Stream #0.1[0x83]: Audio: ac3, 48000 Hz, stereo, 192 kb/s
  Stream #0.2[0x82]: Audio: ac3, 48000 Hz, stereo, 192 kb/s
  Stream #0.3[0x81]: Audio: ac3, 48000 Hz, stereo, 192 kb/s
  Stream #0.4[0x80]: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Unknown codec 'libx264'
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:22:28, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mpeg, from 'title1.vob':
  Duration: 02:18:24.7, start: 0.049756, bitrate: 5645 kb/s
  Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x576, 9800 kb/s, 25.00 fps(r)
  Stream #0.1[0x83]: Audio: ac3, 48000 Hz, stereo, 192 kb/s
  Stream #0.2[0x82]: Audio: ac3, 48000 Hz, stereo, 192 kb/s
  Stream #0.3[0x81]: Audio: ac3, 48000 Hz, stereo, 192 kb/s
  Stream #0.4[0x80]: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Unknown codec 'libx264'

```

now I've tried compiling ffmpeg using hte guide on the cummunity doc but the spt-get source method isn't working and the SVN wont compile.

Any ideas?

---

### Post by FakeOutdoorsman on 2008-07-21
What is the ffmpeg command you used?  Which version of ffmpeg are you using now (Ubuntu repository, Medibuntu repository, daily tarball/SVN)?

---

