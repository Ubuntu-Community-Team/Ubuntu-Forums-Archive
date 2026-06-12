---
title: "Convert video to audio use ffmpeg?"
date: 2010-07-15
forum: Multimedia Software
---

### Post by rudysuryanto on 2010-07-15
Dear all, I want to convert all video file in folder a become audio file in folder b use ffmpeg, how to type it in terminal? Thank's.

---

### Post by andrea000 on 2010-07-16
First are you using the FFmpeg in synaptic or did you install from subversion?The FFmpeg in synaptic i don't think has libmp3lame enabled in it.Here is FakeOutdoorsman [guide]("http://ubuntuforums.org/showthread.php?t=786095") to installing FFmpeg from subversion.There is a gui for ffmpeg if you don't know the terminal commands very well it's called winff it will convert video's to audio using ffmpeg and does a really good job if your converting a lot of files.There may be another way to do it from the terminal faster maybe FakeOutdoorsman will jump in and help you with this one.

---

### Post by nothingspecial on 2010-07-16
I am assuming that you would like to convert avi to mp3

cd to the directory containing the videos

copy this

```
#!/bin/bash
for f in *.avi
do
ffmpeg -i "$f" -ab 128kb "${f%.avi}.mp3"
done;
```

Type ```
nano avi2mp3.sh
```

Paste that into it. Press Ctrl O to save, Enter then Ctrl X to exit

Type ```
chmod +x avi2mp3.sh
```

To make it executable

Then type ./avi2mp3.sh 

Go away, make a cup of tea, come back and you will have mp3s of all your videos \\:D/

---

### Post by rudysuryanto on 2010-07-16
after I  implemented your suggestion, then appears:

FFmpeg version SVN-r24262, Copyright (c) 2000-2010 the FFmpeg developers
  built on Jul 16 2010 19:53:46 with gcc 4.4.3
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50.22. 0 / 50.22. 0
  libavcodec    52.83. 0 / 52.83. 0
  libavformat   52.73. 0 / 52.73. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.22. 0 /  1.22. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[flv @ 0x9e03470] Estimating duration from bitrate, this may be inaccurate

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (2997/50) -> 29.92 (359/12)
Input #0, flv, from '&#21331;&#20381;&#23159; (Timi Zhuo) - &#23567; &#22478; &#25925; &#20107; (Story of a small town).flv':
  Metadata:
    duration        : 162
    starttime       : 0
    totalduration   : 162
    width           : 640
    height          : 360
    videodatarate   : 575
    audiodatarate   : 115
    totaldatarate   : 696
    framerate       : 30
    bytelength      : 14114187
    canseekontime   : true
    sourcedata      : BD075FD46MM
    purl            : 
    pmsg            : 
  Duration: 00:02:41.66, start: 0.000000, bitrate: 705 kb/s
    Stream #0.0: Video: h264, yuv420p, 640x360 [PAR 1:1 DAR 16:9], 588 kb/s, 29.92 tbr, 1k tbn, 59.94 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 117 kb/s
[NULL @ 0x9dfa3e0] [Eval @ 0xbf994d6c] Invalid chars 'b' at the end of expression '128kb'
[NULL @ 0x9dfa3e0] Unable to parse option value "128kb"
Invalid value '128kb' for option 'ab'


How to solve this problem? thank's.

---

### Post by nothingspecial on 2010-07-16
Well it`s saying it doesn`t like the b in ab 128kb (which works for me, but anyway) remove the b and try again, the one after the k not the one after the a.

---

### Post by rudysuryanto on 2010-07-16
Now I know to solve that problem by change the source code to this:

#!/bin/bash
for f in *.*
do
ffmpeg -i "$f" -vn -ar 44100 -ac 2 -ab 192 -f mp3 "${f%.*}.mp3"
done;

if I want to change all video format to mp3

---

### Post by nothingspecial on 2010-07-16
Cool :p

---

### Post by rudysuryanto on 2010-07-16
I also  have  changed the source code like your suggestion to:

#!/bin/bash
for f in *.*
do
ffmpeg -i "$f" -ab 128k "${f%.*}.mp3"
done;

and  this also works, thanks  for all your guidance.:p

---

