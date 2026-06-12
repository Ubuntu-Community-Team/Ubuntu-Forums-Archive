---
title: "symbol lookup error: ./ffmpeg: undefined symbol: frame_hook_add"
date: 2010-02-18
forum: Multimedia Software
---

### Post by rahul23 on 2010-02-18
whenever i am trying to use ffmpeg for watermark getting folowing error

**command used**
```
ffmpeg -i ~/Desktop/ffmpegPrac/input/test.mpg -vhook '/home/rootadmin/Desktop/myffmpeg/test3/lib/vhook/watermark.so -f /home/rootadmin/Desktop/ffmpegPrac/watermark/overlay.png -m 1 -t222222' -an mm.flv
```

**Error got :**
```

symbol lookup error: ./ffmpeg: undefined symbol: frame_hook_add

```

[B]
ffmpeg complete information [/B]

> FFmpeg version 0.5, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/home/rootadmin/Desktop/myffmpeg/test3/ --enable-shared --enable-gpl --enable-nonfree --enable-pthreads --enable-vhook --enable-postproc --enable-avfilter-lavf --enable-avfilter --enable-bzlib --enable-libamr-nb --enable-libamr-wb --enable-libdc1394 --enable-libdirac --enable-libfaac --enable-libfaad --enable-libfaadbin --enable-libgsm --enable-libmp3lame --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-libxvid --enable-zlib --enable-swscale
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Feb 18 2010 15:03:52, gcc: 4.4.1
At least one output file must be specified


I have installed ffmpeg many times but still facing the same problem . plz help
Thanks in advance

---

### Post by rahul23 on 2010-02-20
bump !
i dont know C , so plz guid me to fix this issue

---

### Post by mc4man on 2010-02-20
Why you're installing to a dir. on your desktop don't know, but that's your choice I guess.

Anyway you are building ffmpeg as shared, you should just be doing a static build, then you wouldn't have these ld issues.

---

### Post by rahul23 on 2010-02-20
> **mc4man said:**
> Why you're installing to a dir. on your desktop don't know, but that's your choice I guess.

Anyway you are building ffmpeg as shared, you should just be doing a static build, then you wouldn't have these ld issues.


i am compiling it as shared coz in future i  may need to use php-ffmpeg module  of php.
but will give static  a  try for a  temporary solution.

---

### Post by rahul23 on 2010-02-25
> **mc4man said:**
> Why you're installing to a dir. on your desktop don't know, but that's your choice I guess.

Anyway you are building ffmpeg as shared, you should just be doing a static build, then you wouldn't have these ld issues.

yes thanks man , static compiling just worked out of the box.

---

