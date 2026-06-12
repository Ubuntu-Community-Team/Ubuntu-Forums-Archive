---
title: "ffmpeg flv to mp4"
date: 2009-08-23
forum: Multimedia Software
---

### Post by PaulusEm on 2009-08-23
Hey,

I'm trying to convert my videos with ffmpeg from FLV to mp4 (want to play them on my iPod) using:

```
ffmpeg -i INPUT.FLV -f mp4 -vcodec libx264 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 OUTPUT.MP4
``` but getting the following output:

```
root@server02:~/ffmpeg# ffmpeg -i INPUT.FLV -f mp4 -vcodec libx264 -maxrate 1000k -b 700k -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac -ab 192 -s 320x240 -aspect 4:3 OUTPUT.MP4
FFmpeg version SVN-r19689, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-pthreads --enable-libfaac --enable-libfaad --enable-libmp3lame --enable-libtheora --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.32. 0
  libavformat   52.38. 0 / 52.38. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Aug 23 2009 20:41:18, gcc: 4.2.4 (Ubuntu 4.2.4-1ubuntu4)

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 59.75 (239/4)
Input #0, flv, from 'INPUT.FLV':
  Duration: 00:01:57.55, start: 0.000000, bitrate: 818 kb/s
    Stream #0.0: Video: flv, yuv420p, 480x368, 818 kb/s, 59.75 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 44100 Hz, 2 channels, s16
  Metadata
    hasKeyframes    : true
    audiodatarate   : 96
    hasVideo        : true
    stereo          : true
    canSeekToEnd    : false
    framerate       : 30
    audiosamplerate : 44000
    videocodecid    : 2
    datasize        : 13251723
    lasttimestamp   : 118
    audiosamplesize : 16
    audiosize       : 1463171
    hasAudio        : true
    audiodelay      : 0
    videosize       : 11787178
    metadatacreator : inlet media FLVTool2 v1.0.6 - http://www.inlet-media.de/flvtool2
    lastkeyframetimestamp: 116
    height          : 368
    filesize        : 13283812
    hasMetadata     : true
    audiocodecid    : 2
    videodatarate   : 800
    duration        : 118
    hasCuePoints    : false
    width           : 480
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
[libx264 @ 0x9bc9ab0]broken ffmpeg default settings detected
[libx264 @ 0x9bc9ab0]use an encoding preset (vpre)
Output #0, mp4, to 'OUTPUT.MP4':
    Stream #0.0: Video: libx264, yuv420p, 320x240 [PAR 1:1 DAR 4:3], q=3-5, 700 kb/s, 90k tbn, 59.75 tbc
    Stream #0.1: Audio: aac, 44100 Hz, 2 channels, s16, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
```

Installed ffmpeg via the following tutorial:
[http://ubuntuforums.org/showpost.php?p=6963607&postcount=360](http://ubuntuforums.org/showpost.php?p=6963607&postcount=360)

Hope that somebody can tell me what I'm doing wrong :)

---

### Post by FakeOutdoorsman on 2009-08-23
> **PaulusEm said:**
> 
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s

FFmpeg gave some clues.  FFmpeg wants you to use kilobits/sec if you declare a bitrate, but you only gave it bits/sec for your *-ab* and *-bufsize*.  You just need to add a "k" like you did with *-b* and *-maxrate*.

> [libx264 @ 0x9bc9ab0]broken ffmpeg default settings detected
[libx264 @ 0x9bc9ab0]use an encoding preset (vpre)
You should be using the libx264 presets when using the libx264 encoder.  For iPod 320x240 you could use:
```
ffmpeg -i input.flv -acodec libfaac -ab 96k -ac 2 -vcodec libx264 -vpre hq -vpre ipod320 -threads 0 -crf 22 output.mp4
```
See more examples at:
[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)
and
[FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/)

---

### Post by Shapierian on 2009-08-26
Also the FFmpeg AAC encoder is kind of crappy at the moment. I'm working on making it better but consider yourself warned.

---

### Post by Huss on 2009-09-26
Thanks for the posts. It worked for me.

I found that I needed to rename input files to remove spaces. Also, that the preset '-vpre hq -vpre...' returned an error. After getting rid of the preset and renaming the files it worked beautifully

---

