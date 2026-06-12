---
title: "problems converting flv to avi [ffmpeg]"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by wizardforce on 2007-03-03
thanks in advance!

[edgy fit ubuntu]

I am having problems converting flv files to avi.  I tried to do the conversion via ffmpeg although every time I attempt to do the conversion I get the "I/O error occured
Usually that means that input file is truncated and/or corrupted." error message.  I tried several different files, I even considered that the names themselves were causing problems and tried a test file [one I knew to work in windows], downloaded and named it without any spaces or weird characters- still didn't work, so I looked at the command I was using to convert with ffmpeg:

ffmpeg -i examplevideo.flv examplevideo.avi

I suspect that there is something lacking in the command I used although I really dont know how to fix it if it was.  is there any way that I can troubleshoot this or another method of converting the file?

---

### Post by Prometheus.172214 on 2007-03-03
Well I am not sure of the command line form of the conversion since I am new to Linux, but I came across this online portal ([www.vixy.net](www.vixy.net)) which is an online FLV to AVI converted. Maybe this could help. I have not given it a try though.

---

### Post by wizardforce on 2007-03-03
ya, I have tried the online file converter for flv, I just have a few flv that are a bit tricky to find again- I needed a local way to convert the files for when I can't find the originals again online.

---

### Post by Prometheus.172214 on 2007-03-03
Hmmm .... Is it possible for you to upload one file to some place and give me a link. A small file should do, to find out where it is getting mooted. FLV uses a frameset renderer and AVI I believe uses a pinset renderer. So, maybe there is something you need to change or you might need some lib for it.  Also, this will sound down right mundane, but have you checked the acess permissions for the folder where the files are and the files? You might want to try running this as a super user. (This I have no idea if it makes a difference, but if it is some thing weird like permission, su should work)

---

### Post by stooshbunutu on 2008-02-28
use[ WinFF]("http://biggmatt.com/files/winff-0.33-i386.deb") a front end for the ffmpeg codec to convert the initial video format the desired format. It's the one I use for .flv

Hope this helps :)

---

### Post by erginemr on 2008-02-28
> **stooshbunutu said:**
> use[ WinFF]("http://biggmatt.com/files/winff-0.33-i386.deb") a front end for the ffmpeg codec to convert the initial video format the desired format. It's the one I use for .flv

Hope this helps :)

+1 to that.

---

### Post by FakeOutdoorsman on 2008-02-29
WinFF is a nice program, but If ffmpeg can't convert this file and the command syntax is correct, then WinFF won't work either. The ffmpeg command you used should have worked.  It would have created a mpeg4 avi file using defaults for whatever parameters you didn't specify.  The ffmpeg error you are getting means that your flv file is probably corrupted.  What does ffmpeg say when you try this?

```
ffmpeg -i examplevideo.flv
```

That will let us know that ffmpeg thinks of your file.  For example mine says this (from a youtube video):
```
ffmpeg -i hamointment.flv 
FFmpeg version SVN-r11879, Copyright (c) 2000-2008 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-libvorbis --enable-libtheora --disable-debug --enable-libmp3lame --enable-libfaad --enable-libfaac --enable-pthreads --enable-libx264 --disable-ffserver --disable-ffplay --disable-ipv6 --disable-vhook
  libavutil version: 49.6.0
  libavcodec version: 51.50.0
  libavformat version: 52.7.0
  libavdevice version: 52.0.0
  built on Feb  7 2008 21:30:02, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, flv, from 'hamointment.flv':
  Duration: 00:08:04.5, start: 0.000000, bitrate: 64 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240 [PAR 0:1 DAR 0:1], 29.92 tb(r)
    Stream #0.1: Audio: mp3, 22050 Hz, mono, 64 kb/s
Must supply at least one output file
```

---

