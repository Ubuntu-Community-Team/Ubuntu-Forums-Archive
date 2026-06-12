---
title: "ffmpeg keeps crashing"
date: 2006-06-26
forum: Multimedia &amp; Video
---

### Post by schleppel on 2006-06-26
I'm trying to convert a mpeg-1 video to mpeg-2, but ffmpeg seg faults crashes almost immediately.
```

ffmpeg -i test.mpg -target pal-dvd dvd.mpg
ffmpeg version CVS, build 3276800, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --extra-cflags=-fomit-frame-pointer -DRUNTIME_CPUDETECT --build i486-linux-gnu --enable-gpl --enable-pp --enable-zlib --enable-vorbis --enable-libogg --enable-theora --enable-a52 --enable-dts --enable-dc1394 --enable-libgsm --disable-debug --prefix=/usr
  built on Nov 24 2005 10:19:02, gcc: 4.0.3 20051121 (prerelease) (Ubuntu 4.0.2-4ubuntu3)
Input #0, mpeg, from 'test.mpg':
  Duration: 00:00:36.2, start: 0.638378, bitrate: 16258 kb/s
  Stream #0.0[0x1e0]: Video: mpeg1video, yuv420p, 512x384, 25.00 fps, 800 kb/s
  Stream #0.1[0x1c0]: Audio: mp2, 32000 Hz, stereo, 64 kb/s
Output #0, dvd, to 'dvd.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x576, 25.00 fps, q=2-31, 6000 kb/s
  Stream #0.1: Audio: ac3, 48000 Hz, stereo, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
Segmentation fault

```

On my laptop it works without problems - both kubuntu dapper drake.
Edit: converting the file with the windows version of ffmpeg using wine works fine.

---

### Post by hanzomon4 on 2006-07-31
How do you get the windows version of ffmpeg.
I can't find it.

---

### Post by listerthrawn on 2007-01-13
I know this thread is old but I thought I'd share my experiences.

I was encoding with ffmpeg on a desktop and got seg fault every time i encoded a video, at the same point every time.  The exact same file encoded fine on my laptop.

Desktop was dapper, laptop edgy.

OK, so I upgrade the desktop to edgy, install ffmpeg from source on both machines, and nothing.  Same fault same place.

The only thing I could find different was the Kernel that was installed on each.  Desktop had the 386, laptop generic.

I updraded the desktop to generic and voila, no more problems.

The moral of this story, do a uname -r and see what you're running!  If it's 386 at the end, it may be your problem.

hope this helps!

Chris

---

### Post by zgornel on 2007-01-14
> **hanzomon4 said:**
> How do you get the windows version of ffmpeg.
I can't find it.
Try ffdshow in windows.

---

### Post by robertmf on 2007-10-09
> **listerthrawn said:**
>  

The only thing I could find different was the Kernel that was installed on each.  Desktop had the 386, laptop generic.

I updraded the desktop to generic and voila, no more problems.

The moral of this story, do a uname -r and see what you're running!  If it's 386 at the end, it may be your problem.

hope this helps!

Chris
[COLOR="DarkRed"]
I'm getting the segmentation fault error with Feisty.[/COLOR]

```

2.6.20-16-generic

```:confused:

---

