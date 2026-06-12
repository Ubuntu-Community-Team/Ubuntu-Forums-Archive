---
title: "Issues while converting 192 kbps mp3 using ffmpeg"
date: 2010-06-09
forum: Multimedia Software
---

### Post by arjunak01 on 2010-06-09
I'm having issues while converting 192kbps mp3 using ffmpeg. The right channel somehow gets damaged. I'm using winff and I'm facing this problem only when using mp3 files having bit rate of 192 kbps . i've attached the screenshots of the file . Should i report a bug??

---

### Post by FakeOutdoorsman on 2010-06-09
> **arjunak01 said:**
> I'm having issues while converting 192kbps mp3 using ffmpeg. The right channel somehow gets damaged. I'm using winff and I'm facing this problem only when using mp3 files having bit rate of 192 kbps . i've attached the screenshots of the file . Should i report a bug??

I've never seen FFmpeg do this before.  I would like to attempt to duplicate this.  Questions:
[list][*] What version of Ubuntu are you using?
[*] What version of WinFF are you using?
[*] What WinFF preset are you using?
[*] Can you provide a sample of the original file? 
[*] Did you try using FFmpeg by itself?
[*] Can you show some more details about the original file? You can do this with:[/list]
```
ffmpeg -i input.foo
```
**input.foo** should be the name of your input file.

---

### Post by arjunak01 on 2010-06-09
i'm using ubuntu 10.04 x64 and here is the output 
```
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3
Input #0, mp3, from '/home/arjun//City of Blinding lights.mp3':
  Duration: 00:05:52.00, start: 0.000000, bitrate: 192 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 192 kb/s
At least one output file must be specified

```

---

