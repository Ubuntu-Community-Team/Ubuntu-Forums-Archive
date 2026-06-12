---
title: "create or get a new version of ffmpeg"
date: 2008-09-26
forum: Multimedia Software
---

### Post by cazz on 2008-09-26
Hi
in my ffmpeg I have on my ubuntu I dont have "-sws_flags" but I like to have that.
I have try to create a new ffmpeg but never get that to work with -sws_flag so I'm hopping someone can tell me how to do it or if I can download a deb file of ffmpeg that have that.

---

### Post by FakeOutdoorsman on 2008-09-26
You have two options: use a third-party, precompiled version of ffmpeg, such as the one from [Medibuntu]("http://medibuntu.org/"), or you can compile it yourself.  Medibuntu's ffmpeg has been compiled with "--enable-swscaler", which is what you need I believe.  If you want to compile the latest SVN of ffmpeg yourself, refer to:
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

---

### Post by cazz on 2008-09-26
Hmm strange I add the repositories and update and that and then use sudo apt-get install ffmpeg but it still say 

```
ffmpeg: unrecognized option '-sws_flags'
```

and when I open the Synaptic it say in version "3:0.cvs20070307-Subuntu7.1+medibuntu1"

I maybe have to try again to compile my own ffmpeg
but I have no idea what to install.
I just know that in ./configure I have to add "--enable-swscaler" but I think I have to install something more then just that you have write in your howto?

```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:21:25, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, avi, from '/media/disk/mymovie.avi':
  Duration: 01:34:44.4, start: 0.000000, bitrate: 925 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 768x576, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 112 kb/s
ffmpeg: unrecognized option '-sws_flags'

```

---

### Post by cazz on 2008-09-27
is very strange.
I have try sometime now but still same problem.
When I try it on my windows with ffmpeg that can run on win32 it works nice but I like to use my ubuntu computer.

I fix it with 

[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg) "Compiling ffmpeg from upstream svn snapshots"

and

[http://ubuntuforums.org/showthread.php?p=5680964](http://ubuntuforums.org/showthread.php?p=5680964)

:)

---

### Post by FakeOutdoorsman on 2008-09-28
> **cazz said:**
> Hmm strange I add the repositories and update and that and then use sudo apt-get install ffmpeg but it still say 
```
ffmpeg: unrecognized option '-sws_flags'
```


I'm guessing that swscaler will be used by default if it you use --enable-swscaler during installation configuration.  I don't think there is a "-sws_flags" option with a recent version of ffmpeg.

---

