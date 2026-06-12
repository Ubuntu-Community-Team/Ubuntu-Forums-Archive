---
title: "DeVeDeNG Error When Running FFMPEG"
date: 2020-11-22
forum: Multimedia Software
---

### Post by uRock on 2020-11-22
I am running devedeng 4.8.1 in Xubuntu 18.04

I get the follow error when it goes to convert MP4. I had previously gotten the same error at the end of conversion of MKV.  

```
ffmpeg version 3.4.8-0ubuntu0.2 Copyright (c) 2000-2020 the FFmpeg developers
  built with gcc 7 (Ubuntu 7.5.0-3ubuntu1~18.04)
  configuration: --prefix=/usr --extra-version=0ubuntu0.2 --toolchain=hardened --libdir=/usr/lib/x86_64-linux-gnu --incdir=/usr/include/x86_64-linux-gnu --enable-gpl --disable-stripping --enable-avresample --enable-avisynth --enable-gnutls --enable-ladspa --enable-libass --enable-libbluray --enable-libbs2b --enable-libcaca --enable-libcdio --enable-libflite --enable-libfontconfig --enable-libfreetype --enable-libfribidi --enable-libgme --enable-libgsm --enable-libmp3lame --enable-libmysofa --enable-libopenjpeg --enable-libopenmpt --enable-libopus --enable-libpulse --enable-librubberband --enable-librsvg --enable-libshine --enable-libsnappy --enable-libsoxr --enable-libspeex --enable-libssh --enable-libtheora --enable-libtwolame --enable-libvorbis --enable-libvpx --enable-libwavpack --enable-libwebp --enable-libx265 --enable-libxml2 --enable-libxvid --enable-libzmq --enable-libzvbi --enable-omx --enable-openal --enable-opengl --enable-sdl2 --enable-libdc1394 --enable-libdrm --enable-libiec61883 --enable-chromaprint --enable-frei0r --enable-libopencv --enable-libx264 --enable-shared
  libavutil      55. 78.100 / 55. 78.100
  libavcodec     57.107.100 / 57.107.100
  libavformat    57. 83.100 / 57. 83.100
  libavdevice    57. 10.100 / 57. 10.100
  libavfilter     6.107.100 /  6.107.100
  libavresample   3.  7.  0 /  3.  7.  0
  libswscale      4.  8.100 /  4.  8.100
  libswresample   2.  9.100 /  2.  9.100
  libpostproc    54.  7.100 / 54.  7.100
Expected int64 for vol but found 268.8
```

I know that it can process MP4, because I did a test with some smaller videos I had creating during screen recordings.

Any ideas on what may be missing would be greatly appreciated.

---

### Post by Yellow Pasque on 2020-11-25
> Expected int64 for vol but found 268.8

It looks like either something is wrong with the source file or the program is trying to use ffmpeg incorrectly.

---

### Post by Yellow Pasque on 2020-11-25
Maybe this will have some clues:
[https://trac.ffmpeg.org/wiki/AudioVolume](https://trac.ffmpeg.org/wiki/AudioVolume)
[http://trac.ffmpeg.org/ticket/1070](http://trac.ffmpeg.org/ticket/1070)

---

### Post by uRock on 2020-11-26
Thanks for that! Oddly enough, when I reduced from doing two video clips on the disk image to just one, it almost worked. It wasn't happy with the subtitle file I had put together.

I am going to install 20.04 on another computer and see if it has the same problems.

---

### Post by uRock on 2020-11-27
Don't laugh, but I think the issues was fixed by a restart. Did the weekly reboot and the files that were causing problems are no longer causing problems.

---

