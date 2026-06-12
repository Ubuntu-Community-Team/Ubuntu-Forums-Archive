---
title: "How to compress DV for storage"
date: 2008-12-23
forum: Multimedia Software
---

### Post by DrSpirograph on 2008-12-23
Hi,
I've taken some DV footage that I'd like to compress and store on my computer. The DV footage was imported by Apple's iMovie, and from there I exported it to full quality DV footage.

When I try to encode it with ffmpeg though, I get a series of "AC EOB marker is absent pos=64" errors and ffmpeg bails out. When I playback the converted footage, it appears to be only about 1 frame long. (The original is about 30 minutes, so it's a bit short).

I can playback the original just fine using xine (it still outputs the AC EOB marker errors messages, but that doesn't stop it from playing).

Below is the command I used and the output.

```
ffmpeg -i rehearse.dv -vcodec xvid -acodec mp3 -b 2000k -ac 2 -ab 128k -vtag DX50 -qmin 5 test.avi
```

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, dv, from 'rehearse.dv':
  Duration: 00:42:04.6, start: 0.000000, bitrate: 28800 kb/s
  Stream #0.0: Video: dvvideo, yuv420p, 720x576, 28800 kb/s, 25.00 fps(r)
  Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, 1536 kb/s
Output #0, avi, to 'test.avi':
  Stream #0.0: Video: xvid, yuv420p, 720x576, q=5-31, 2000 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=66
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
AC EOB marker is absent pos=64
frame=    1 q=5.0 Lsize=      45kB time=0.0 bitrate=9267.6kbits/s
video:34kB audio:1kB global headers:0kB muxing overhead 27.586112%
```

Any suggestions on how I can get this going?
I'd prefer to use ffmpeg because the command line options are much simpler, but if anyone's got suggestions for how to do it with encoders like transcode or mencoder - so far I've had no luck with any of them.

I've tried googling, but come up nil.

Cheers for any help.

---

