---
title: "Error Converting Flash Video"
date: 2010-04-04
forum: Multimedia Software
---

### Post by Cygnia on 2010-04-04
Greetings, I'm trying to convert downloaded Flash videos to mp4. I first tried WinFF (a front-end to ffmpeg) and got an error message, so then I tried using ffmpeg directly in the terminal, only to get the same message. I remember doing this same thing in the past with no problems, so something must be wrong. I'm on Karmic 64 bit. The message I get is the following:

FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:35:00, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 47.94 (23969/500) -> 23.98 (24000/1001)
Input #0, flv, from 'Space Junk Song':
  Duration: 00:02:27.19, start: 0.000000, bitrate: 547 kb/s
    Stream #0.0: Video: h264, yuv420p, 640x360 [PAR 1:1 DAR 16:9], 547 kb/s, 23.98 tbr, 1k tbn, 47.94 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16
Output #0, mp4, to 'SJS.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 640x360 [PAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 23.98 tbc
    Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1

Any help with this would be appreciated. Thanks.

---

### Post by ron999 on 2010-04-04
Hi
Try a command like this:-
```
ffmpeg -i filename.flv -acodec copy -vcodec copy filename.mp4
```

You should end up with an mp4 file with h264 video and aac audio.
No converting is necessary.

---

### Post by Cygnia on 2010-04-04
Thanks ron999, although in the terminal this results in a similar error message about the frame rate and the unsupported codec, it does produce a usable file that I can play. Thanks again.

---

### Post by ron999 on 2010-04-04
You're welcome.

---

