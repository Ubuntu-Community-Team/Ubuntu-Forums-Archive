---
title: "Video conversion software"
date: 2009-09-23
forum: Multimedia Software
---

### Post by arnab_das on 2009-09-23
I have been searching for video conversion softwares ever since the time I installed Ubuntu. So far I have tested Avidemux, devede, and a few others. However the thing is none of them is able to "properly" convert files to .avi

There seems to be a certain problem with .avi getting stuck all the time. However mpeg2 conversion is near perfect with Videomax.

Plz suggest a video conversion software, something like convertx on windows.

---

### Post by Keith Hedger on 2009-09-23
If you are OK with the command line install ffmpeg it will convert just about anything to anything and there are plenty of tips and tutorials on the forums to help you out

---

### Post by arnab_das on 2009-09-23
> **Keith Hedger said:**
> If you are OK with the command line install ffmpeg it will convert just about anything to anything and there are plenty of tips and tutorials on the forums to help you out

i downloaded winff, which i presume is basically a GUI version of ffmepg.

the thing is, i think there might be some problem with Ubuntu's ffmpeg codec itself! (i'm not sure of it obviously) the fact is, no matter what video converter i use, it always manages to have these strange picture artifacts which become more prominent when i watch them on a hi def television. (mind u i dont get these when i'm watching the converted video on my PC)

plz help me out.

---

### Post by SuperSonic4 on 2009-09-23
I assume the original video displays without a hitch on your HDTV?

It could simply be a resolution problem. Arch's ffmpeg works fine and it's likely to be the same ffmpeg. What does ```
ffmpeg -version
``` say? Mine is below


```
[22:06:20] sonic ~ $  ffmpeg -version
FFmpeg version 0.5, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --prefix=/usr --enable-gpl --enable-libmp3lame --enable-libvorbis --enable-libfaac --enable-libfaad --enable-libxvid --enable-libx264 --enable-libtheora --enable-postproc --enable-shared --enable-pthreads --enable-x11grab --enable-swscale
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 18 2009 20:24:32, gcc: 4.3.3
FFmpeg 0.5
libavutil     49.15. 0 / 49.15. 0
libavcodec    52.20. 0 / 52.20. 0
libavformat   52.31. 0 / 52.31. 0
libavdevice   52. 1. 0 / 52. 1. 0
libswscale     0. 7. 1 /  0. 7. 1
libpostproc   51. 2. 0 / 51. 2. 0

```

---

### Post by arnab_das on 2009-09-23
mine's here: 

```
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
FFmpeg 0.5-svn17737+3:0.svn20090303-1ubuntu6
libavutil     49.15. 0 / 49.15. 0
libavcodec    52.20. 0 / 52.20. 0
libavformat   52.31. 0 / 52.31. 0
libavdevice   52. 1. 0 / 52. 1. 0
libavfilter    0. 4. 0 /  0. 4. 0
libswscale     0. 7. 1 /  0. 7. 1
libpostproc   51. 2. 0 / 51. 2. 0

```

and yes, the original video plays fine on my television.
and whats the resolution problem? I'm using 720x576 as the output resolution.

---

### Post by SuperSonic4 on 2009-09-23
Mine is slightly newer but the ffmpeg changelog describes little new. What filetype are you converting from?

---

### Post by arnab_das on 2009-09-23
> **SuperSonic4 said:**
> Mine is slightly newer but the ffmpeg changelog describes little new. What filetype are you converting from?

some hi def mkv files, captured from a friend's hi def video camera. trying to convert them to standard res as my dvd player wont play mkv.

---

### Post by SuperSonic4 on 2009-09-23
Have you thought about using devede (from the repos) to make a disc image of the mkv files and burning it to dvd rather than converting?

For resolution chances are your tv uses a different resolution such as 1440x900 for example

---

### Post by arnab_das on 2009-09-23
> **SuperSonic4 said:**
> Have you thought about using devede (from the repos) to make a disc image of the mkv files and burning it to dvd rather than converting?

For resolution chances are your tv uses a different resolution such as 1440x900 for example

i have used devede. but it crashes very often, also doesnt have many customization options. i'll try it once more and let u know. btw my hdtv is hd ready,720p. so that'd be 1366x768. and same goes for my monitor.

---

### Post by arnab_das on 2009-09-23
wow! devede works perfectly!

thank u thank u thank u! :)

---

