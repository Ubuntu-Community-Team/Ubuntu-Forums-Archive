---
title: "making dvd"
date: 2008-10-16
forum: Multimedia Software
---

### Post by neba on 2008-10-16
I have some home videos and I want to format them so I can play them on my dvd play. Right now its is formated with '.ogv' I have tried burning them to the cd and it wont work. Any thoughts?
thanks neba

---

### Post by cariboo on 2008-10-16
You would be better of converting to avi and then burning a dvd. Use this command to convert from ogv to avi:

```
ffmpeg -i input.ogv output.avi
``` then use a program like devede to convert from avi to dvd format.

ffmpeg and devede are both available in the repositories.

Jim

---

### Post by neba on 2008-10-18
thank you. Is there any think I need to add to that code? I put in the command as you posted and this is what I got.

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 29 2008 18:28:49, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
input.ogv: I/O error occured
Usually that means that input file is truncated and/or corrupted.

I know that the file is not corrupted and I don't know if it is truncated. 

thanks neba

---

### Post by neba on 2008-11-21
I just used this code 'ffmpeg -i input.ogv output.avi' every thing worked just fine, but when I went to watch the movie, it is all pixelated. the quality is now really poor amd the movie changed from 600mb to 200mb. 
any thoughts?
thanks Neba

---

### Post by neba on 2008-11-28
please help. I really need help on this.

---

