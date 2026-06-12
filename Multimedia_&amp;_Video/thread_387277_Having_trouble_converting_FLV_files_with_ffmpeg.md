---
title: "Having trouble converting FLV files with ffmpeg"
date: 2007-03-18
forum: Multimedia &amp; Video
---

### Post by Inbo on 2007-03-18
I'm having trouble converting FLV videos. I can play them in VLC player.. :

```
mik@mik-desktop:~$ ffmpeg -i video.flv -ab 56 -ar 22050 -b 500 -s 320x240 video.mpg
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2004 Fabrice Bellard
  configuration:  --enable-gpl --enable-pp --enable-pthreads --enable-vorbis --enable-libogg --enable-a52 --enable-dts --enable-libgsm --enable-dc1394 --disable-debug --enable-mp3lame --enable-faadbin --enable-faad --enable-faac --enable-xvid --enable-amr_nb --enable-shared --prefix=/usr 
  libavutil version: 0d.49.0.0
  libavcodec version: 0d.51.11.0
  libavformat version: 0d.50.5.0
  built on Mar 17 2007 23:11:09, gcc: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
video.flv: I/O error occured
Usually that means that input file is truncated and/or corrupted.
mik@mik-desktop:~$ 

```

I'm using the source build from the ffmpeg site

---

### Post by Inbo on 2007-03-18
nvm.. I got it to work (finally, after trying to figure this thing out for atleast 3 hours).

---

### Post by exidez on 2007-04-28
could you please share how you did it?

---

### Post by peacechicken on 2007-05-02
Yes I'd like to know how you fixed it as well...

---

