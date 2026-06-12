---
title: "Convert flv to mpeg2"
date: 2008-12-09
forum: Multimedia Software
---

### Post by ronnielsen1 on 2008-12-09
I'm trying to change some flv videos to be able to play on a dvd player and after numerous attempts and googling I was able to play a lower quality dvd. I was trying to use dvdauthor for my latest attempt but it insists on mpeg2 files and not the avi or mpq I'm ending up with. Does anyone have any advice?

---

### Post by Matt Yun on 2008-12-09
> **ronnielsen1 said:**
> I'm trying to change some flv videos to be able to play on a dvd player and after numerous attempts and googling I was able to play a lower quality dvd. I was trying to use dvdauthor for my latest attempt but it insists on mpeg2 files and not the avi or mpq I'm ending up with. Does anyone have any advice?

A suggestion from a [discussion at the Puppy Linux forums]("http://www.murga-linux.com/puppy/viewtopic.php?t=29216&sid=e24a62a6eae49d0fdb36aff79a3ec4c0").  One of the posts suggests the following ffmpeg command for converting flv to mpeg-2:

 ```
ffmpeg -i file.flv -ab 128 -ar 44100 -b 500 -ac 2 -s 320x240 file.mpg
```

If commandline is not your thing, there is a Linux GUI for Mencoder:  [AutoMen for Linux.]("http://www.videohelp.com/forum/archive/automen-5-3-for-linux-t358755.html")  I think it's Free software, but I'm not sure.  According to [this review]("http://www.freewaregenius.com/2008/10/30/automen-a-small-yet-brilliant-video-converter/"), it supports flv

If you get really stuck, there's a freeware program called [Mediacoder]("http://mediacoder.sourceforge.net"), [which mostly works with WINE]("http://forum.mediacoderhq.com/viewtopic.php?t=2275").  Apparently, it [converts from flv to mpeg-2]("http://mediacoder.sourceforge.net/wiki/index.php/Converting_Examples").
 
A basic ffmpeg how-to from Ubuntu Geek:  [http://www.ubuntugeek.com/convert-flv-google-videos-to-mpg-using-ffmpeg.html](http://www.ubuntugeek.com/convert-flv-google-videos-to-mpg-using-ffmpeg.html)

---

### Post by piratebill on 2008-12-09
[http://mediacoder.sourceforge.net/](http://mediacoder.sourceforge.net/)


run this with wine.  It works amazingly!

[EDIT]

I should really learn to read previous posts completely ^_^

---

### Post by ronnielsen1 on 2008-12-10
Shouldn't the resolution be increased to 720 x 480?

---

### Post by ronnielsen1 on 2008-12-10
Ok, I was able to change the videos but is there a way to increase resolution so the dvd has a good picture?

---

### Post by FakeOutdoorsman on 2008-12-10
The target option in ffmpeg will automatically set the other options (frame size, bitrate, codecs, buffer sizes) and make an appropriate output:
```
ffmpeg -i input.flv -target dvd output.mpg
```

---

### Post by ronnielsen1 on 2008-12-11
> ffmpeg -i input.flv -target dvd output.mpg


This works great on some but on others it returns an error similar to:

>  ffmpeg -i Walkin_down_the_road.flv -target dvd WalkingDownTheRoad.mpg
FFmpeg version SVN-r13582, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --prefix=/usr --libdir=${prefix}/lib --shlibdir=${prefix}/lib --bindir=${prefix}/bin --incdir=${prefix}/include/ffmpeg --enable-shared --enable-libmp3lame --enable-gpl --enable-libfaad --mandir=${prefix}/share/man --enable-libvorbis --enable-pthreads --enable-libfaac --enable-libxvid --enable-postproc --enable-libamr-nb --enable-libamr-wb --enable-x11grab --enable-libgsm --enable-libx264 --enable-liba52 --enable-libtheora --extra-cflags=-Wall -g -fPIC -DPIC --cc=ccache cc --enable-swscale --enable-libdc1394 --enable-nonfree --disable-mmx --disable-stripping --enable-avfilter --enable-libdirac --disable-decoder=libdirac --enable-libschroedinger --disable-encoder=libschroedinger --disable-altivec --disable-armv5te --disable-armv6 --disable-vis
  libavutil version: 49.7.0
  libavcodec version: 51.58.0
  libavformat version: 52.16.0
  libavdevice version: 52.0.0
  libavfilter version: 0.0.0
  built on Oct 22 2008 15:22:08, gcc: 4.3.2

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 30.00 (30/1)
Input #0, flv, from 'Walkin_down_the_road.flv':
  Duration: 00:02:00.51, start: 0.000000, bitrate: 8 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x436, 30.00 tb(r)
    Stream #0.1: Audio: mp3, 22050 Hz, mono, 8 kb/s
Could not determine norm (PAL/NTSC/NTSC-Film) for target.
Please prefix target with "pal-", "ntsc-" or "film-",
or set a framerate with "-r xxx".


I've experimented with a few ntsc options and I didn't guess right. 
I'm also wondering. When playing the videos in VLC they're still not real good video (yes, it does change it to dvd resolution) Is there a way to get a better picture or to have a smaller size video (Not take up the whole tv) in order to have a better picture?

---

### Post by stinger30au on 2008-12-11
winff may help

gui for ffmeg with a ton of presets

[http://www.biggmatt.com/winff-04/](http://www.biggmatt.com/winff-04/)

---

### Post by FakeOutdoorsman on 2008-12-11
> **ronnielsen1 said:**
> I've experimented with a few ntsc options and I didn't guess right. I'm also wondering. When playing the videos in VLC they're still not real good video (yes, it does change it to dvd resolution) Is there a way to get a better picture or to have a smaller size video (Not take up the whole tv) in order to have a better picture?
Try this:
```
ffmpeg -i input.flv -target ntsc-dvd -padtop 120 -padbottom 120 -padleft 180 -padright 180 -s 360x240 output.mpg
```
It declares a frame rate and adds black padding to cover the rest of the screen.

---

