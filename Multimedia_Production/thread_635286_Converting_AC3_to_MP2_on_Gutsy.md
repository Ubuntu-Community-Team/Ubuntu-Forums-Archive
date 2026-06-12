---
title: "Converting AC3 to MP2 on Gutsy"
date: 2007-12-08
forum: Multimedia Production
---

### Post by pt123 on 2007-12-08
When I was using Fiesty I used to convert AC3 files to MP2. 
ffmpeg -i in.ac3 -ab 256 -acodec mp2 out.mp2

But I have noticed after upgrading to gutsy I cannot convert anymore.
```

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
Input #0, ac3, from 'GRand DesignExeter.ac3':
  Duration: 00:47:10.4, start: 0.000000, bitrate: 448 kb/s
  Stream #0.0: Audio: 0x0000, 48000 Hz, stereo, 448 kb/s
Output #0, mp2, to 'out.mp2':
  Stream #0.0: Audio: mp2, 48000 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Unsupported codec (id=86020) for input stream #0.0


```

It is telling up **Unsupported codec (id=86020) for input stream**

There seem to be a similar bug reported here
[https://bugs.launchpad.net/medibuntu/+bug/164206](https://bugs.launchpad.net/medibuntu/+bug/164206)

Is there a solution apart from 
"ffmpeg from using an older version."

which is messy.


--
[http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-March/002426.html](http://lists.mplayerhq.hu/pipermail/ffmpeg-user/2006-March/002426.html)
From this thread 
> 
"./configure --enable-mp3lame --enable-gpl --enable-faac --enable-xvid  
--extra-cflags=-DHAVE_LRINTF
and just add:
--enable-a52

Is there a place where we can complain to the person that creates these DEBs?

---

### Post by tengil on 2007-12-09
I'm having problems getting ffmpeg and ffmpeg2theora to read ac3 in gutsy as well.

---

### Post by ArkRoyal on 2008-01-02
the reason is ac3 was not compiled into ffmpeg when it was created.  am looking for a way to do that now.  there is no nice --enable-ac3 in the configure --help and  --enable-liba52 didn't cut it.  I took a look at the configuration output on the fiesty version of ffmpeg and its says nothing.

---

### Post by pt123 on 2008-01-02
If you look at the mediubuntu launch pad it is now there in those reps.

That said I am sure Feisty had the ability.

---

### Post by tengil on 2008-01-03
There was a medibuntu update in gutsy just before christmas which added AC3 to the ffmpeg utilities. The problem on my side with the new version however is that the oggs coming out of ffmpeg2theora has a/v out of sync. I've tested with a clip which transcoded ok before the xmas update.

---

### Post by eye208 on 2008-01-03
> **pt123 said:**
> When I was using Fiesty I used to convert AC3 files to MP2. 
ffmpeg -i in.ac3 -ab 256 -acodec mp2 out.mp2

But I have noticed after upgrading to gutsy I cannot convert anymore.
You can use MEncoder to convert.

I guess AC3 support was dropped from Gutsy's ffmpeg package to keep it in the universe repo (MEncoder is in multiverse). However, Gutsy's MEncoder still provides the full transcoding feature set, so ffmpeg is kind of redundant anyway.

---

