---
title: "How to convert avi to mp4."
date: 2008-05-10
forum: Multimedia Software
---

### Post by pisio on 2008-05-10
Hi 4 all.
My English is not perfect, and you  can't understand me , please don't read  the  post.



I've hot Ubuntu 8.04 and wont to convert  movies for my PSP.From Google  i give  ```
pisio@gaara:~/&#1055;&#1083;&#1086;&#1090;$ ffmpeg -i 1.avi -title "Naruto Test" -vcodec mpeg4 -acodec aac -b 672k -ab 96k -r 30000/1001 -ar 24000 -s 320x240 -aspect 16:9 -g 300 -aic 2 -mbd 2 -cmp 3 -precmp 3 -subcmp 3 -trellis 2 -flags +4mv+trell -f psp M4V00001.MP4

```
But result is :
```
pisio@gaara:~$ cd /home/pisio/&#1055;&#1083;&#1086;&#1090;/
pisio@gaara:~/&#1055;&#1083;&#1086;&#1090;$ ffmpeg -i 1.avi -title "Naruto Test" -vcodec mpeg4 -acodec aac -b 672k -ab 96k -r 30000/1001 -ar 24000 -s 320x240 -aspect 16:9 -g 300 -aic 2 -mbd 2 -cmp 3 -precmp 3 -subcmp 3 -trellis 2 -flags +4mv+trell -f psp M4V00001.MP4
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Mar 12 2008 14:31:53, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu4)
Input #0, avi, from '1.avi':
  Duration: 00:42:36.8, start: 0.000000, bitrate: 902 kb/s
  Stream #0.0: Video: h264, yuv420p, 856x480, 23.98 fps(r)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Unknown codec 'aac'
pisio@gaara:~/&#1055;&#1083;&#1086;&#1090;$ 

```


How I can convert the movie in mp4 for  psp ....
Please help me ....

If I false  the forum , please  move my  post.

---

### Post by shirilover on 2008-05-11
You could try avidemux, it's in the repositories.
It has two PSP presets for auto-configurating the encoding process.

Or use -acodec faac instead.

---

### Post by pisio on 2008-05-11
```
************
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 128 kb/s
Unknown codec 'faac'
pisio@gaara:~/&#1055;&#1083;&#1086;&#1090;$
```
Wiht Avidemux  -> PSP call  "Broken file"


Maybe I must installl  win XP :-k and convert AVi-to-mp4 with  PSPvideo9....
Ubuntu have option to install under win,  is it ?

---

### Post by myspacejmagenst on 2008-10-12
I use VirtualBox to run XP. I still don't have Ubuntu figured out. I am learning as I go.

---

### Post by tqft on 2008-10-12
I am using handbrake
[http://handbrake.fr/](http://handbrake.fr/)

to rip videos (avi, dvds, etc) to mp4 for my ipod.

Linux is command line only unless you want to download, compile and install from source.

Binary here
[http://handbrake.fr/rotation.php?file=HandBrake-0.9.2_i386.tar.gz](http://handbrake.fr/rotation.php?file=HandBrake-0.9.2_i386.tar.gz)

---

### Post by DirtDawg on 2008-10-12
Do you have libfaac installed?
```
sudo apt-get install libfaac0
```
Not sure it will solve the problem, but it looks like you might be missing a codec.

---

