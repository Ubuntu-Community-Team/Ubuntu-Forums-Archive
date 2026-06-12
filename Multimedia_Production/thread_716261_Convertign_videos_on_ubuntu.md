---
title: "Convertign videos on ubuntu"
date: 2008-03-05
forum: Multimedia Production
---

### Post by searayman on 2008-03-05
I need to convert wmv videos in .mov for a mac on my ubuntu computer. Is there any easy way to do this?

THanks

---

### Post by Creative2 on 2008-03-06
command line resolutions

install ffmpeg from medibuntu repo...

ffmpeg -i INPUT -r 25 -f mov -vcodec mpeg4 -ar 22050 -b 700k -acodec aac -ab 128k -y OUTPUT.mov

or this 

ffmpeg -i INPUT    OUTPUT.mov

or install fuoco tools (on windows that mov works)

or install winff on repository it should convert into mov

---

### Post by searayman on 2008-03-06
> **Creative2 said:**
> command line resolutions

install ffmpeg from medibuntu repo...

ffmpeg -i INPUT -r 25 -f mov -vcodec mpeg4 -ar 22050 -b 700k -acodec aac -ab 128k -y OUTPUT.mov

or this 

ffmpeg -i INPUT    OUTPUT.mov

or install fuoco tools (on windows that mov works)

or install winff on repository it should convert into mov

ok so i installed ffmpeg and tried to convert but it didnt work....


```
mike@mike-desktop:~$ cd Desktop/
mike@mike-desktop:~/Desktop$ ffmpeg -i WINTER\ TRACK\ 08\ .wmv wtrack.mov
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jun  3 2007 20:59:25, gcc: 4.1.3 20070528 (prerelease) (Ubuntu 4.1.2-9ubuntu2)

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 30.00 (30/1)
Input #0, asf, from 'WINTER TRACK 08 .wmv':
  Duration: 00:28:09.7, start: 1.579000, bitrate: 2071 kb/s
  Stream #0.0: Audio: wmav2, 44100 Hz, stereo, 160 kb/s
  Stream #0.1: Video: wmv3, yuv420p, 640x480, 30.00 fps(r)
Output #0, mov, to 'wtrack.mov':
  Stream #0.0: Video: mpeg4, yuv420p, 640x480, q=2-31, 200 kb/s, 30.00 fps(c)
  Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Unsupported codec for output stream #0.1
mike@mike-desktop:~/Desktop$ 

```

---

### Post by Creative2 on 2008-03-06
install ffmpeg after you have turned on medibuntu repository....

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by searayman on 2008-03-06
> **Creative2 said:**
> install ffmpeg after you have turned on medibuntu repository....

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

so should i uninstall it and then mediabuntu thing then re-install it?

---

### Post by Creative2 on 2008-03-06
just turn on medibuntu repository then you should only update your ffmpeg

---

### Post by searayman on 2008-03-08
Ok si i did this command to convert:

```
ffmpeg -i INPUT OUTPUT.mov
```

and it worked, but the output quality was extremely bad. It made the videos super pixely and I need to put these videos on DVD's

SO any suggestions how to do this and keep quality?


THanks

---

### Post by Creative2 on 2008-03-08
ffmpeg -i INPUT -r 25    -ar 44100 -b 900k  -ab 256k -y OUTPUT.mov

or with 30 frame for second

ffmpeg -i INPUT -r 30    -ar 44100 -b 900k  -ab 256k -y OUTPUT.mov

---

### Post by searayman on 2008-03-08
> **Creative2 said:**
> ffmpeg -i INPUT -r 25    -ar 44100 -b 900k  -ab 256k -y OUTPUT.mov

or with 30 frame for second

ffmpeg -i INPUT -r 30    -ar 44100 -b 900k  -ab 256k -y OUTPUT.mov 
ok, cool but i just upgraded to 8.04 so is there a way to get mediabuntu repo on it?

---

