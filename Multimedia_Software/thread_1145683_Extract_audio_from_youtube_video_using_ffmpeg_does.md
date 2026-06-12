---
title: "Extract audio from youtube video using ffmpeg does not work"
date: 2009-05-01
forum: Multimedia Software
---

### Post by gsub on 2009-05-01
Hi, all.

I get the youtube video like so: After opening the link to the video, I wait for the video to DL. I then copy  /tmp/FlashXXXXX to another location - ~/sandbox/abc.flv

Then, I try to run

ffmpeg -i abc.flv abc.mp3, and I get the following error messages:

```
FFmpeg version r11872+debian_3:0.svn20080206-12ubuntu3.1, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-x11grab --prefix=/usr --enable-libgsm --enable-libtheora --enable-libvorbis --enable-pthreads --disable-strip --enable-libfaad --enable-libfaadbin --enable-liba52 --enable-liba52bin --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Mar 13 2009 17:48:10, gcc: 4.3.2
[flv @ 0x4181aa28]Unsupported video codec (7)
[flv @ 0x4181aa28]Unsupported audio codec (a)
[flv @ 0x4181aa28]Unsupported video codec (7)
...
...
...
[flv @ 0x4181aa28]Unsupported video codec (7)
[flv @ 0x4181aa28]Unsupported video codec (7)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, flv, from 'v.flv':
  Duration: 00:05:25.6, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: 0x0007, 25.00 tb(r)
    Stream #0.1: Audio: 0x000a, 44100 Hz, stereo
Output #0, mp2, to 'jam.mp3':
    Stream #0.0: Audio: mp2, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec (id=0) for input stream #0.1


```

It seems like I dont have the right codecs installed, but when I open the .flv with totem or vlc, they play quite nicely.

Just wondering if someone knows which codec to install.

Many thanks.

---

### Post by gsub on 2009-05-02
<bump>

---

### Post by andrew.46 on 2009-05-03
Hi gsub,

I suspect that your copy of FFmpeg is lacking some vital pieces. Have a look at this guide for more information and a fix:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

All the best,

Andrew

---

