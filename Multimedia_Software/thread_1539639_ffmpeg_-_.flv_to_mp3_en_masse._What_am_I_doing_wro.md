---
title: "ffmpeg - .flv to mp3 en masse. What am I doing wrong?"
date: 2010-07-26
forum: Multimedia Software
---

### Post by RabbitWho on 2010-07-26
Hi guys, 
I'm changing flvs to mp3s en masse using ffmpeg, it's working but the mp3s that are getting made have no sound... they have pictures.. it's fecked.. what am I doing wrong?

Here's the code I'm using
```

for i in *.flv; do ffmpeg -i "$i" -f mp3 -vcodec libxvid -acodec libfaac -ar 22050 `basename $i .flv`-`date +%H%M%S%N`.mp3; done
```

Here's what's happening:
```

rabbit@penguincounter:~/Music/MusicFromFriends/ennio$ for i in *.flv; do ffmpeg -i "$i" -f mp3 -vcodec libxvid -acodec libfaac -ar 22050 `basename $i .flv`-`date +%H%M%S%N`.mp3; done
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, flv, from 'A_Fistful_of_Dollars_1964__-_Suite__PART_1_-1.flv':
  Duration: 00:05:54.22, start: 0.000000, bitrate: 177 kb/s
    Stream #0.0: Video: flv, yuv420p, 320x240, 113 kb/s, 29.97 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 64 kb/s
Output #0, mp3, to 'A_Fistful_of_Dollars_1964__-_Suite__PART_1_-1-005509420764337.mp3':
    Stream #0.0: Video: libxvid, yuv420p, 320x240, q=2-31, 200 kb/s, 90k tbn, 29.97 tbc
    Stream #0.1: Audio: libfaac, 22050 Hz, mono, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
[libxvid @ 0x1abd420]Invalid pixel aspect ratio 0/1
Video encoding failed
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 2000.00 (2000/1) -> 29.92 (359/12)
Input #0, flv, from 'A_Fistful_of_Dollars_1964__-__Suite__PART_2_.flv':
  Duration: 00:07:47.86, start: 0.000000, bitrate: 194 kb/s
    Stream #0.0: Video: h264, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 194 kb/s, 29.92 tbr, 1k tbn, 2k tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
Output #0, mp3, to 'A_Fistful_of_Dollars_1964__-__Suite__PART_2_-005509587479765.mp3':
    Stream #0.0: Video: libxvid, yuv420p, 320x240 [PAR 1:1 DAR 4:3], q=2-31, 200 kb/s, 90k tbn, 29.92 tbc
    Stream #0.1: Audio: libfaac, 22050 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
frame=13999 fps=315 q=29.0 Lsize=   15157kB time=467.93 bitrate= 265.4kbits/s    
video:11505kB audio:3652kB global headers:0kB muxing overhead 0.000206%
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

```

Why's the output fecked? Ideas?

---

### Post by ron999 on 2010-07-26
The bit in the middle is wrong.

Change this
```
[SIZE="5"]-vcodec libxvid -acodec libfaac -ar 22050[/SIZE]
```
into this
```
[SIZE="5"]-vn -acodec libmp3lame[/SIZE]
```
Then try again.

---

### Post by RabbitWho on 2010-07-26
Thank you! :D:KS:D

Finished command: 
```

for i in *.flv; do ffmpeg -i "$i" -f mp3 -vn -acodec libmp3lame `basename $i .flv`-`date +%H%M%S%N`.mp3; done

```this should work for anyone. Just cd to the folder you want to do the business on. 

Marking thread as solved.

---

### Post by FakeOutdoorsman on 2010-07-26
Your command is encoding at the default of **64 kb/s**, which may be considered low quality depending on the source.  Adding *-aq 4* will sound better and is similar to *lame -V 4* (you could also just decare an audio bitrate like *-ab 160k*):
```
for i in *.flv; do ffmpeg -i "$i" -f mp3 -vn -acodec libmp3lame -aq 4 `basename $i .flv`-`date +%H%M%S%N`.mp3; done
```

It appears that your FLV files, or at least some of them, already have MP3 audio.  If they are all like this then you can simply copy the audio stream instead of re-encoding:
```
for i in *.flv; do ffmpeg -i "$i" -acodec copy `basename $i .flv`-`date +%H%M%S%N`.mp3; done
```
This will be much faster and also preserve the quality because you will avoid re-encoding.  Of course it won't work well if your inputs have something other than MP3 audio.

---

### Post by waldir on 2011-07-19
> **RabbitWho said:**
> 
Finished command: 
```

for i in *.flv; do ffmpeg -i "$i" -f mp3 -vn -acodec libmp3lame `basename $i .flv`-`date +%H%M%S%N`.mp3; done

```this should work for anyone. Just cd to the folder you want to do the business on. 

Marking thread as solved.

Actually, this command doesn't work for me if the input filenames have spaces. [This post]("http://ubuntuforums.org/showpost.php?p=8976474&postcount=5") seems to have a better way:
```
for f in *.flv; do ffmpeg -i "$f" -acodec libmp3lame -ab 128k "${f%.flv}.mp3"; done
```

---

