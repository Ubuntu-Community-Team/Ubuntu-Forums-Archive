---
title: "converting from ogv to avi !!"
date: 2010-05-06
forum: Multimedia Software
---

### Post by MEGA. on 2010-05-06
Hello guys,

every time i try to convert from ogv to avi file using ffmpeg on ubuntu 10.04, this was working on 9.10 

the output avi file comes out looks like this 

[IMG]http://img683.imageshack.us/img683/7968/screenshot3t.png[/IMG]

---

### Post by ivanblago on 2010-05-06
It is a same problem with my system.....

and I use this ogv to flv converter [http://gtk-apps.org/content/show.php?content=90837](http://gtk-apps.org/content/show.php?content=90837)

this converter convert the .ogv file first to .avi and then to flv,,,,,,,,,, just copy the temp .avi file and its ok.

---

### Post by FakeOutdoorsman on 2010-05-06
> **MEGA. said:**
> Hello guys,

every time i try to convert from ogv to avi file using ffmpeg on ubuntu 10.04, this was working on 9.10

Can you provide your FFmpeg command and the complete FFmpeg output?

---

### Post by xzero1 on 2010-05-06
Its a known ffmpeg bug. See [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2258700.html]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2258700.html")

---

### Post by MEGA. on 2010-05-06
> **ivanblago said:**
> It is a same problem with my system.....

and I use this ogv to flv converter [http://gtk-apps.org/content/show.php?content=90837](http://gtk-apps.org/content/show.php?content=90837)

this converter convert the .ogv file first to .avi and then to flv,,,,,,,,,, just copy the temp .avi file and its ok.

THank You, it's good, but Flv output quality not really good.
thanks any way man

---

### Post by MEGA. on 2010-05-06
> **FakeOutdoorsman said:**
> Can you provide your FFmpeg command and the complete FFmpeg output?

command used 
ffmpeg -i /home/moh/out-1.ogv /home/moh/out.ogv

and here is the full complete ffmpeg output :

```
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
Input #0, ogg, from '/home/mb/Desktop/1.ogv':
  Duration: 00:01:27.66, start: 0.000000, bitrate: 741 kb/s
    Stream #0.0: Invalid Codec type -1
    Stream #0.1: Video: theora, yuv420p, 1280x800, PAR 1:1 DAR 8:5, 15 tbr, 15 tbn, 15 tbc
    Stream #0.2: Audio: vorbis, 22050 Hz, mono, s16, 89 kb/s
Output #0, avi, to '/home/moh/Desktop/11.avi':
    Stream #0.0: Video: mpeg4, yuv420p, 1280x800 [PAR 1:1 DAR 8:5], q=2-31, 200 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: mp2, 22050 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.2 -> #0.1
[mpeg4 @ 0x8444940]removing common factors from framerate
Press [q] to stop encoding
frame=  425 fps= 73 q=2.0 Lsize=    2719kB time=87.25 bitrate= 255.3kbits/s    
video:1957kB audio:682kB global headers:0kB muxing overhead 3.031703%

```

---

### Post by MEGA. on 2010-05-06
> **xzero1 said:**
> Its a known ffmpeg bug. See [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2258700.html]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2258700.html")

thanks man for the link, I post the output for the command there.!!

---

### Post by MEGA. on 2010-05-07
Is there any other application i can use to convert with high quality??

---

### Post by Bonster on 2010-05-07
use Devede app, divx mode

---

### Post by MEGA. on 2010-05-07
> **Bonster said:**
> use Devede app, divx mode

Thanks Bonster :)

---

### Post by Kilz on 2010-06-07
> **Bonster said:**
> use Devede app, divx mode

Thanks from me also. Just goes to show that one answer can help different people. I had a ogv that wouldn't transcode with Arista and the video came out like the first poster when I tried the command line. Since I had Devede is was simple to try it, and it worked.

---

