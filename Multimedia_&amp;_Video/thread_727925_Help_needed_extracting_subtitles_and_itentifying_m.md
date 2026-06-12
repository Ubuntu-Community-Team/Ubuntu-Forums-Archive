---
title: "Help needed extracting subtitles and itentifying media file."
date: 2008-03-18
forum: Multimedia &amp; Video
---

### Post by theolster on 2008-03-18
Hi,

I've got quite a few mpeg files that I recovered from my old dvb mythtv box after a hardware failure.  The problem is I don't really know what sort of file it is, I presume it's an mpeg2 but could be wrong.

Anyway, the reason I want to know is that I want to put together a script to batch convert these to xvid avii, and whilst the audio and video is perfect there seems to be no way to extract the subtitles.  I've opened up the original mpeg in vlc and can toggle the subtitles on and off successfully, so I know that they are there.

A lot of my results from googling only seem to come up with subtitles from dvds not mpegs, please help.

Thanks,
Ollie

---

### Post by takayuki on 2008-03-18
have you tried

ffmpeg -i filename

this should tell you about the file.

---

### Post by theolster on 2008-03-18
I tried that, and all I get is errors:```
$ ffmpeg -i filename.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)
filename.mpg: I/O error occured
Usually that means that input file is truncated and/or corrupted.
```
This happens for every file, so no more info.  Except that it might be an MPEG-1 file...? St least that's how filezilla identifies it.

---

### Post by takayuki on 2008-03-18
i may be sending you in the wrong direction here... but i've used [this version]("http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu/") of ffmpeg for awhile with great results

[http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu/](http://po-ru.com/diary/fixing-ffmpeg-on-ubuntu/)

---

