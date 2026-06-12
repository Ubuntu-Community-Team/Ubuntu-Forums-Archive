---
title: "WinFF doesn't work anymore"
date: 2008-10-29
forum: Multimedia Software
---

### Post by fantan on 2008-10-29
Hi,

Can anybody help me?
On my Ubuntustudio 8.04.1 I used the WinFF long time for convert flv's to mp3. The program worked fine all the time. 
I can't remember when, but some time ago after automatic upgrade WinFF don't want to work anymore. When I try to convert flv to mp3, I get the similar error message:

"FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Sep 26 2008 12:56:27, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu1)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, flv, from '/Flv/Video/Kormorán/Kormorán_Három_határ.flv':
  Duration: 00:04:18.1, start: 0.000000, bitrate: 64 kb/s
  Stream #0.0: Video: flv, yuv420p, 320x240, 25.00 fps(r)
  Stream #0.1: Audio: mp3, 22050 Hz, mono, 64 kb/s
Output #0, mp2, to '/home/albert/Zene/Kormorán_Három_határ.mp3':
  Stream #0.0: Audio: 0x0000, 44100 Hz, stereo, 160 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Unsupported codec for output stream #0.0
Press Enter to Continue"

Till upgrading the program worked fine, but after upgrade it doesn't.
Can anybody help me, what to do?

Thanks for advance!

fantan

---

### Post by paul.gevers on 2008-12-04
Because winff works closely with ffmpeg it is more likely that the problem is in an update of ffmpeg (the interface changed). You can check [http://code.google.com/p/winff/wiki/InstallPresetsxml](http://code.google.com/p/winff/wiki/InstallPresetsxml) for instructions to update your presets.xml file.

---

