---
title: "convert video file to dvd iso on dual core"
date: 2007-12-31
forum: Multimedia Production
---

### Post by kefurd06 on 2007-12-31
k here's what i want to do: convert one or more avi files to a dvd iso (playable in a normal dvd player). i also want it to utilize my dual cores. anyone have a solid solution? i will accept CLI responses! thanks.

---

### Post by nzadLithium on 2007-12-31
[http://www.cyberciti.biz/tips/howto-linux-create-video-dvds.html](http://www.cyberciti.biz/tips/howto-linux-create-video-dvds.html)

a tutorial

---

### Post by kefurd06 on 2007-12-31
> **nzadLithium said:**
> [http://www.cyberciti.biz/tips/howto-linux-create-video-dvds.html](http://www.cyberciti.biz/tips/howto-linux-create-video-dvds.html)

a tutorial

i followed this tutorial until i got an unsupported codec error. here are my results:

```

kevin@dv9000:~/torrents/Interview[2007]DvDrip AC3[Eng]-FXG$ ffmpeg -i out.avi -y -target ntsc-dvd -sameq -aspect 16:9 out.mpgFFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (24000/1001)
Input #0, avi, from 'out.avi':
  Duration: 01:24:29.4, start: 0.000000, bitrate: 1157 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 656x368, 23.98 fps(r)
  Stream #0.1: Audio: 0x2000, 48000 Hz, 5:1, 448 kb/s
Output #0, dvd, to 'out.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x480, q=2-31, 6000 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=86020) for input stream #0.1

```

Here are the stats for the video file from nautilus properties:
```

Video Codec: ISO MPEG-4 (XviD, ffmpeg)
Audio Codec: A/52 5.1

```

---

### Post by Creative2 on 2007-12-31
Search ConvertIT or Fuoco tools

---

### Post by crush304 on 2008-01-01
> **kefurd06 said:**
> i followed this tutorial until i got an unsupported codec error. here are my results:

```

kevin@dv9000:~/torrents/Interview[2007]DvDrip AC3[Eng]-FXG$ ffmpeg -i out.avi -y -target ntsc-dvd -sameq -aspect 16:9 out.mpgFFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (24000/1001)
Input #0, avi, from 'out.avi':
  Duration: 01:24:29.4, start: 0.000000, bitrate: 1157 kb/s
  Stream #0.0: Video: mpeg4, yuv420p, 656x368, 23.98 fps(r)
  Stream #0.1: Audio: 0x2000, 48000 Hz, 5:1, 448 kb/s
Output #0, dvd, to 'out.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 720x480, q=2-31, 6000 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: ac3, 48000 Hz, 5:1, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=86020) for input stream #0.1

```

Here are the stats for the video file from nautilus properties:
```

Video Codec: ISO MPEG-4 (XviD, ffmpeg)
Audio Codec: A/52 5.1

```
are you using the ffmpeg from the metibuntu repo [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

if you just want to make an iso for a dvd, try DeVeDe

sudo apt-get install devede

---

### Post by kefurd06 on 2008-01-01
> **crush304 said:**
> are you using the ffmpeg from the metibuntu repo [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

if you just want to make an iso for a dvd, try DeVeDe

sudo apt-get install devede

i've tried devede, and it failed me. for one it created a 1.8 gig iso instead of ~4.3 gigs, and the video glitched throughout the movie. is there a fix for either of those problems?

i just installed dvd flick under wine and it seems to work. it does exactly what i need, exactly right, and it's completely free. i've wasted enough of my time looking for a linux alternative to nero vision/win dvd maker.

---

### Post by crush304 on 2008-01-02
> **kefurd06 said:**
> i've tried devede, and it failed me. for one it created a 1.8 gig iso instead of ~4.3 gigs, and the video glitched throughout the movie. is there a fix for either of those problems?

i just installed dvd flick under wine and it seems to work. it does exactly what i need, exactly right, and it's completely free. i've wasted enough of my time looking for a linux alternative to nero vision/win dvd maker.

if you want to make a bigger file you can up the bitrate, although from the post above it looks like the file you are converting from is only ~1000 kb/s, bigger doesn't necessarily mean better, 

I'm not sure about the glitches (I'm no video expert)

---

### Post by ~LoKe on 2008-01-02
I wrote a script that basically combines that guide into one command, and I'm using all the packages from medibuntu and it works just fine.  Do you have the latest ffmpeg?

---

### Post by ArkRoyal on 2008-01-02
You have to recompile ffmpeg to include ac3 support.  I found this thread while searching how to do that.  There is no nice --include-ac3 in the config options.  And so far using  --enable-liba52 did not work.  But that is what needs to happen to get ac3 to work.  This info came off the ffmpeg mailing list.

---

