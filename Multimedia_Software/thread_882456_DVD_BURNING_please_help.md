---
title: "DVD BURNING please help"
date: 2008-08-07
forum: Multimedia Software
---

### Post by Kilroth on 2008-08-07
Okay, I just burned a DVD. I used TUVID. Everything worked out like a charm
execpt the audio. It was out of sync with the video. I ran the AVI file that I had of the movie and that was synced nicely. So i know it has to be with the encoding. I am a Poor boy and I know you get what you pay for but is there a codec that I can tell it to us or a better program that I can use that might be open source  thank you

---

### Post by yabbies on 2008-08-07
ffmpeg
it's a part of Tovid so you already have it. Just open a terminal and enter the command.

```

ffmpeg -i your_movie.avi -y -target ntsc-dvd -sameq -aspect 16:9 your_movie.mpg
```

---

### Post by Kilroth on 2008-08-07
I typed that in and I got this 

ffmpeg -i Heavy.Metal.2000.640.25fps.1019kbps.v5.WunDeeSee.avi -y -target ntsc-dvd -sameq -aspect 16:9 Heavy.Metal.2000.640.25fps.1019kbps.v5.WunDeeSee.mpg-
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Heavy.Metal.2000.640.25fps.1019kbps.v5.WunDeeSee.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.

I know the video and audio are not corrupted I watched the movie on my computer

---

### Post by Drezliok on 2008-08-08
I would also like to know why my sound is off.

---

### Post by yabbies on 2008-08-08
you have a space in your avi

> ffmpeg -i Heavy.Metal.2000.640.25fps.1019kbps.v5.WunDeeSee.**a vi** -y -target ntsc-dvd -sameq -aspect 16:9 

---

### Post by Kilroth on 2008-08-08
Ok so I tried to fix the .avi and it still gives me an I/O error 
I was told by mky friend that It might be a sound codec if that is the case what should i do 






-y -target ntsc-dvd -sameq -aspect 16:9 
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Heavy.Metal.2000.640.25fps.1019kbps.v5.WunDeeSee.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.
paul@turbine:~$

---

### Post by Drezliok on 2008-08-12
BUMP

We both want the answer to the problem.

---

### Post by yabbies on 2008-08-12
```
Heavy.Metal.2000.640.25fps.1019kbps.v5.WunDeeSee.**a vi**: I/O error occured
```

Still have a space in your avi

try renaming your heavymetal file to something easier to type in
for instance just HM.avi

---

### Post by Kilroth on 2008-08-13
Same Error 
paul@turbine:~$ ffmpeg -i HM.avi -y -target ntsc-dvd -sameq -aspect 16:9 HM.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
HM.avi: I/O error occured
Usually that means that input file is truncated and/or corrupted.

---

