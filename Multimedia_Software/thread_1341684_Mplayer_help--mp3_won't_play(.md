---
title: "Mplayer help--mp3 won't play:("
date: 2009-11-30
forum: Multimedia Software
---

### Post by winzer on 2009-11-30
I am trying to convert a youtube video into a mp3 file without success. I am using mplayer. 
I located the video in my /tmp directory and moved it to my Desktop. 
I renamed it vid1.flv
I tried:
```
winzer@winzer-laptop:~/Desktop$ mplayer -dumpaudio vid1.flv -dumpfile audio.mp3
MPlayer SVN-r29237-4.4.1 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing vid1.flv.
libavformat file format detected.
[lavf] Video stream found, -vid 0
[lavf] Audio stream found, -aid 1
VIDEO:  [H264]  320x240  0bpp  25.000 fps  116.4 kbps (14.2 kbyte/s)
Core dumped ;)

Exiting... (End of file)

```
It outputs a mp3 file; the problem is the mp3 file won't play. :(

---

### Post by andrew.46 on 2009-11-30
Hi winzer,

One problem could very well be that the audio may not be mp3 in the first place and if the video is H264 the sound may very well be aac, the *-dumpaudio -dumpfile* settings will not perform a conversion. A better tool would be FFmpeg and I would suggest looking at this guide first:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and then running it across your file as follows:
```

ffmpeg -i vid1.flv
```

This will report the exact makeup of your file and if you like you can post the *complete* terminal output and it should then be a simple matter to suggest syntax to convert the audio stream to mp3.

All the best,

Andrew

---

### Post by winzer on 2009-11-30
> **andrew.46 said:**
> Hi winzer,

One problem could very well be that the audio may not be mp3 in the first place and if the video is H264 the sound may very well be aac, the *-dumpaudio -dumpfile* settings will not perform a conversion. A better tool would be FFmpeg and I would suggest looking at this guide first:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and then running it across your file as follows:
```

ffmpeg -i vid1.flv
```

This will report the exact makeup of your file and if you like you can post the *complete* terminal output and it should then be a simple matter to suggest syntax to convert the audio stream to mp3.

All the best,

Andrew

I went through the tutorial and made the installations. 
I got the following output:
```
chris@chris-laptop:~/Desktop$ ffmpeg -i vid1.flv
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:15:16, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 60.00 (60/1) -> 29.97 (30000/1001)
Input #0, flv, from 'vid1.flv':
  Duration: 00:07:18.69, start: 0.000000, bitrate: 265 kb/s
    Stream #0.0: Video: h264, yuv420p, 854x480 [PAR 1:1 DAR 427:240], 265 kb/s, 29.97 tbr, 1k tbn, 60 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16
At least one output file must be specified

```
So it's aac format?

---

### Post by andrew.46 on 2009-11-30
Hi winzer,

> **winzer said:**
> So it's aac format?

Certainly is, the newer youtube videos tend to be h264 video and aac sound so it was an easy guess :). If you are still keen for mp3 sound try:

```
ffmpeg -i vid1.flv -acodec libmp3lame -ab 128k output.mp3
```

and this should produce your mp3.

All the best,

Andrew

---

