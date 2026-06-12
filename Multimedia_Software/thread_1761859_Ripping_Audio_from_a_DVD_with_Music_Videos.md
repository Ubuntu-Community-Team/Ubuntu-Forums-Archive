---
title: "Ripping Audio from a DVD with Music Videos"
date: 2011-05-18
forum: Multimedia Software
---

### Post by duranl on 2011-05-18
I have a DVD with lots of music videos.  I would like to be able to listen to the songs in my car which can play mp3 files.  Is there a way that I could create mp3 files from the music videos on the DVD?

Thanks in advance :guitar:

---

### Post by jerrrys on 2011-05-19
have not tried it myself, but a good place to start

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=rip+music++dvd&as_qdr=all&sa=Google+Search&lang=en#851](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=rip+music++dvd&as_qdr=all&sa=Google+Search&lang=en#851)

---

### Post by duranl on 2011-05-19
^Thanks for the info.  I was able to get a little further in the process.  

So far, I have used DVDRIP to get the videos from the DVD to my computer.  They are now in vob format.  Any suggestions on how I can convert them to mp3?  I've tried WinFF to convert from vog to mp3, but I get the following error:
> 
FFmpeg version 0.6.2-4:0.6.2-1ubuntu1, Copyright (c) 2000-2010 the Libav developers
  built on Mar 22 2011 15:55:04 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mpeg @ 0x691420]max_analyze_duration reached
Input #0, mpeg, from '/home/lloyd/dvdrip-data/ReggaetonCubano2011/vob/001-C002/ReggaetonCubano2011-001.vob':
  Duration: 00:03:58.97, start: 286.343667, bitrate: 1675 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 352x240 [PAR 10:11 DAR 4:3], 1426 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
**Unknown encoder 'libmp3lame'**
Press Enter to Continue
BTW, I am not violating copyright laws.  This is a DVD from Cuba.

---

### Post by ron999 on 2011-05-19
Hi
The restricted encoders (extra codecs) need to be enabled, that's why you see error **Unknown encoder 'libmp3lame'**
The information is here:-
[http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg+codecs]("http://ubuntuforums.org/showthread.php?t=1117283&highlight=ffmpeg+codecs")

---

### Post by duranl on 2011-05-19
Installed the *unstripped* libraries and it worked perfectly.  Thanks!

---

### Post by andrew.46 on 2011-05-19
The commandline can be a little cumbersome but it is possible to use Transcode to rip and convert the audio from such dvds, the bug advantage being that it is done in a single step.

---

