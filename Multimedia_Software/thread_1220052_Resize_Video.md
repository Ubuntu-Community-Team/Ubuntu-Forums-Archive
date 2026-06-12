---
title: "Resize Video"
date: 2009-07-22
forum: Multimedia Software
---

### Post by radopod on 2009-07-22
Hey guys
I have been reading a lot about video editing as I have suddenly found a small job that needs me to do so. Thanks to helpful posts on this forum I installed kdenlive and was able to successfully join a couple of videos into one. My only question now is how to go about resizing these videos. Their current size is 720X576 pixels. I would like to scale it down to 320X240 in order to reduce their size. Is it possible with kdenlive(had a look at some tutorials but couldn't do much)? Looking forward to getting some help.

Cheers
Imran

---

### Post by FakeOutdoorsman on 2009-07-22
Is this a DV video?  What do you want the final format to be, or what is the final destination of these videos (web, computer, DVD, phone, etc)?  What version of Ubuntu are you using?

---

### Post by radopod on 2009-07-22
It is presently in AVI Format. I plan to put this up on Vimeo for Online viewers. I am currently using 9.04.

---

### Post by SuperSonic4 on 2009-07-22
I'd use ffmpeg 

```
ffmpeg -i input.avi -s 320x240 -aspect 4:3 -vcodec libx264 output.avi
```

ffmpeg is very flexible so you can pick and choose

---

### Post by radopod on 2009-07-22
Thanks a lot for the suggestion! :) I tried it and got this error

```
imran@imran-laptop:/media/disk-1$ ffmpeg -i project_management.avi -s 320x240 -aspect 4:3 -vcodec libx264 management_small.avi
FFmpeg version 0.5-svn17737+3:0.svn20090303-1ubuntu6, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --extra-version=svn17737+3:0.svn20090303-1ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --disable-stripping --disable-vhook --enable-libdc1394 --disable-armv5te --disable-armv6 --disable-armv6t2 --disable-armvfp --disable-neon --disable-altivec --disable-vis --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 10 2009 23:18:41, gcc: 4.3.3
Input #0, avi, from 'project_management.avi':
  Duration: 00:19:30.44, start: 0.000000, bitrate: 30343 kb/s
    Stream #0.0: Video: dvvideo, yuv420p, 720x576, PAR 16:15 DAR 4:3, 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: pcm_s16le, 48000 Hz, stereo, s16, 1536 kb/s
Unknown encoder 'libx264'
```

Checked for libx264 in Synaptic and it seems to be installed.

---

### Post by SuperSonic4 on 2009-07-22
It could have been because of the way you installed ffmpeg - it seems many ubuntu users compile it from standard instead of medibuntu (in arch this problem does not exist)

You could try not putting in the -vcodec libx264 part or try another encoder. 

FYI I suggest you install ffmpeg from the medibuntu repos

---

### Post by FakeOutdoorsman on 2009-07-22
> **SuperSonic4 said:**
> It could have been because of the way you installed ffmpeg - it seems many ubuntu users compile it from standard instead of medibuntu (in arch this problem does not exist)

You could try not putting in the -vcodec libx264 part or try another encoder. 

FYI I suggest you install ffmpeg from the medibuntu repos

There has been no FFmpeg package in the Medibuntu repository since Ubuntu Hardy Heron.  You need to enable restricted encoders.  See option "B" in:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

You'll get better results with the FFmpeg libx264 presets and if you use a more suitable output container:
```
ffmpeg -i project_management.avi -acodec libfaac -ac 2 -ab 128k -ar 44100 -vcodec libx264 -vpre hq -s 640x480 -crf 24 -threads 0 output.mp4
```
See [General compression guidelines for Vimeo](http://vimeo.com/help/compression) for their recommendations.

---

### Post by radopod on 2009-07-28
Exceptional Help! That worked like a charm. :D Thanks a lot.

---

### Post by johntkucz on 2012-03-24
Hey this is a superb thread.  I need to resize vids frequently and love CLI! But alas, how do I find more about using ffmpeg from cli.  The speed of this thread was a bit advanced.  Cheers.  Thanks!

---

### Post by cariboo on 2012-03-24
This three year old thread needs to go back to sleep, @johntkucz, please start a new thread with your question.

---

