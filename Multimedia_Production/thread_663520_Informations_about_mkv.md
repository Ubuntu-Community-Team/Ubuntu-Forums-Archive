---
title: "Informations about mkv"
date: 2008-01-10
forum: Multimedia Production
---

### Post by stocton12 on 2008-01-10
I have a .mkv movie and I want to find out some informations about it, like resolution, video bitrate, audio channels and bitrate. Is there any program that can do that?

---

### Post by Creative2 on 2008-01-10
i don't have mkv file but you could try to use ffmpeg 

ffmpeg -i INPUT  

example 

ffmpeg -i myfileìfalsemp3.mp3

FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-libmp3lame --enable-libfaadbin --enable-libfaad --enable-libfaac --enable-xvid --enable-x264 --enable-liba52 --enable-amr_nb --enable-amr_wb --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Dec 20 2007 21:25:50, gcc: 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Input #0, mp3, from ' /home/Sbucatone/myfileìfalsemp3.mp3':
[B]  Duration: 00:05:21.6, start: 0.000000, bitrate: 64 kb/s
  Stream #0.0: Audio: mp2, 44100 Hz, stereo, 64 kb/s
Must supply at least one output file
[/B]

---

### Post by stocton12 on 2008-01-10
It gives me the same information that xine gives me (resolution and fps). I want also to find out the bitrate in both video and audio.

Duration: 02:10:31.4, bitrate: N/A
  Stream #0.0: Audio: ac3, 48000 Hz, 5:1
  Stream #0.1: Video: h264, yuv420p, 1920x816, 25.00 fps(r)

---

### Post by Creative2 on 2008-01-10
mmm** bitrate: N/A**
ahi ahi ahi !! i don't know other way sorry

---

### Post by yabbies on 2008-01-10
I'm at work but check to see if exiftool handles .mkv

I know it's in the repos

---

