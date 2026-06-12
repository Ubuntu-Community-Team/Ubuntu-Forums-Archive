---
title: "Converting video"
date: 2008-07-28
forum: Multimedia Software
---

### Post by hidarikani on 2008-07-28
So I have a few .avi files from my camera. I want to convert them because a 10 second file weighs 61 MB :o

I have installed WinFF 0.33 on Ubuntu 7.10 x64 but I keep getting the error
```
Unknown codec 'xvid'
```
I have ffmpeg package from medibuntu repository (the free one) installed

How do i fix the error? Are there alternative apps for converting video?

Thanks in advance

---

### Post by Major_Kong on 2008-07-28
Try using mencoder. There's no suitable gui, but using the CLI is not that difficult.

---

### Post by silkstone on 2008-07-28
Several other codec packages are available through Synatpic, in addition to ffmpeg - try these...

sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll w32codecs

---

### Post by wolfen69 on 2008-07-28
ffmpeg works for me. if you want a gui for it, install [winff]("http://winff.googlecode.com/files/winff-0.42-i386.deb") also.

---

### Post by FakeOutdoorsman on 2008-07-28
I'm guessing that the WinFF command is using a different name for the xvid codec for the version of ffmpeg that you are using, or perhaps your ffmpeg is not compiled with xvid support.  You can find out with this command:
```
ffmpeg -formats | grep xvid
```
You should get the following response:
```
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 16 2008 19:54:40, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
  EV    xvid
```
On the second line down (the ffmpeg configuration line) you should see "--enable-xvid" or something similar.  If that is there you know ffmpeg was compiled with xvid.  The last line tells you what ffmpeg calls xvid (just plain "xvid" in the Hardy Heron Medibuntu ffmpeg).  The EV tells you that you can Encode to xvid and that it is a Video codec.

Now check your WinFF preset.  The WinFF 0.42 has this for "XVID in AVI":
```
-r 29.97 -vcodec xvid -vtag XVID -s 640x480 -aspect 4:3 -maxrate 1800k -b 1500k -qmin 3 -qmax 5 -bufsize 4096 -mbd 2 -bf 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -g 300 -acodec mp3 -ar 48000 -ab 128k -ac 2
```
-vcodec should be the same as whatever ffmpeg calls xvid.  If it is different then change it.

---

### Post by cotcot on 2008-07-28
> **hidarikani said:**
> Are there alternative apps for converting video?

Thanks in advance

Avidemux

Fuoco converter

---

