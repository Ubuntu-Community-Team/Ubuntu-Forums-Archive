---
title: "Converting .ogv to watchable .avi"
date: 2010-07-24
forum: Multimedia Software
---

### Post by xpowerfulxx on 2010-07-24
When ever I get a .ogv from something like gtk-recordmydesktop or RecordItNow, I get a .ogv. That's fine, except I would like to upload it to youtube. I use WinFF for my converting, except I get crap quality as I posted an example [here]("http://www.youtube.com/watch?v=wMZR5PxVXPQ").

How do I fix it?

---

### Post by d3v1150m471c on 2010-07-24
```

ffmpeg -i your.ogv -sameq new.avi

```

---

### Post by ron999 on 2010-07-24
> **xpowerfulxx said:**
> 

How do I fix it?

Hi
There's a solution using mencoder in this thread here:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566&highlight=youtube]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566&highlight=youtube")

---

### Post by xpowerfulxx on 2010-07-24
> **d3v1150m471c said:**
> ```

ffmpeg -i your.ogv -sameq new.avi

```
kristopher@ubuntu:~$ ffmpeg /home/kristopher/f.ovg -sameq f.avi
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
Unable to find a suitable output format for '/home/kristopher/f.ovg'

---

### Post by andrew.46 on 2010-07-25
Hi xpowerfulxx,

The command is missing the initial -i and has a typo with the file extension:

```
ffmpeg **[COLOR="Red"]-i[/COLOR]** /home/kristopher/f.**[COLOR="Red"]ovg[/COLOR]** -sameq f.avi
```

I suspect as well you need to have a look at what codecs you are after in your output file instead of simply trusting the defaults... 

Andrew

---

### Post by xpowerfulxx on 2010-07-25
> **andrew.46 said:**
> Hi xpowerfulxx,

The command is missing the initial -i and has a typo with the file extension:

```
ffmpeg **[COLOR=Red]-i[/COLOR]** /home/kristopher/f.**[COLOR=Red]ovg[/COLOR]** -sameq f.avi
```I suspect as well you need to have a look at what codecs you are after in your output file instead of simply trusting the defaults... 

Andrew
Ok I fixed it but I still get the horrible quality with the random colors.

---

### Post by ron999 on 2010-07-25
> **ron999 said:**
> Hi
There's a solution using mencoder in this thread here:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566&highlight=youtube]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566&highlight=youtube")

...

---

### Post by xpowerfulxx on 2010-07-25
> **ron999 said:**
> ...
Worked.
Lock?

---

