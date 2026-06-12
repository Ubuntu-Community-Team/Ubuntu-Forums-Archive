---
title: "Converting youtube videos to PSP compatible videos"
date: 2009-11-03
forum: Multimedia Software
---

### Post by vamshi617 on 2009-11-03
Hi There,

Hope this message finds you well,

 I have tried many things but nothing is working, previously  on ubuntu 9.4, i had a single line of code which used to do the job of converting .flv to .mp4(psp compatible)

but now as i installed 9.10 from the CD and asked it to clear the previous installation, I am unable to find the line of code and now i am back to "square one".

So please point me to any good working tool you might want to suggest ? ):P

---

### Post by vamshi617 on 2009-11-03
**tried **

**ffmpeg -i mantra.flv -b 300 -s 320x240 -vcodec xvid -ab 32 -ar 24000 -acodec aac M4V00010.mp4**

**got error : **
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

Seems stream 0 codec frame rate differs from container frame rate: 2000.00 (2000/1) -> 11.99 (12000/1001)
Input #0, flv, from 'mantra.flv':
  Duration: 00:03:48.49, start: 0.000000, bitrate: 201 kb/s
    Stream #0.0: Video: h264, yuv420p, 320x184 [PAR 1:1 DAR 40:23], 201 kb/s, 11.99 tbr, 1k tbn, 2k tbc
    Stream #0.1: Audio: aac, 22050 Hz, stereo, s16
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
Unknown encoder 'xvid'
jvk@jvk-laptop:~/Videos/forPSP$ ffmpeg -i mantra.flv -b 300 -s 320x240 -vcodec xvid -ab 32 -ar 24000 -acodec aac M4V00010.mp4

**Any suggestions ???? **

---

### Post by FakeOutdoorsman on 2009-11-03
I don't have a PSP, but I would guess copying the video and audio into a MP4 container should suffice since I believe it can handle H.264/AAC:
```
ffmpeg -i mantra.flv -acodec copy -vcodec copy mantra.mp4
```
No re-encoding, so no quality loss.  Also, FFmpeg is attempting to tell you what is wrong with your command:
```
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
```
Add a "k" to your bitrates: *-b 300k* and *-ab 32k*.
```
Unknown encoder 'xvid'
```
There is no encoder named xvid.  See a list of supported encoders with:
```
ffmpeg -formats
```
You may also need to enable restricted formats:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by jlr1701 on 2009-11-04
Not familiar with PSP 3, but there are a few Firefox extensions that will allow you to download videos in MP4 format. I'm currently using the 1-Click YouTube Video Downloader, and it works great.

Hope that helps. :)

---

### Post by vamshi617 on 2009-11-05
> **jlr1701 said:**
> Not familiar with PSP 3, but there are a few Firefox extensions that will allow you to download videos in MP4 format. I'm currently using the 1-Click YouTube Video Downloader, and it works great.

Hope that helps. :)
You are right but PSP needs special treatment, even though I can get MP4 format videos it wont recognise them on my PSP, i says corrupted data, soo.. I need to convert it to a format so that PSP likes it...

---

### Post by DMisigoy on 2009-11-05
vixy.net is a nice app for getting anything off youtube into another format, but that is a windows app.

---

### Post by vamshi617 on 2009-11-05
> **FakeOutdoorsman said:**
> I don't have a PSP 3, but I would guess copying the video and audio into a MP4 container should suffice since I believe it can handle H.264/AAC:
```
ffmpeg -i mantra.flv -acodec copy -vcodec copy mantra.mp4
```
No re-encoding, so no quality loss.  Also, FFmpeg is attempting to tell you what is wrong with your command:
```
WARNING: The bitrate parameter is set too low. It takes bits/s as argument, not kbits/s
```
Add a "k" to your bitrates: *-b 300k* and *-ab 32k*.
```
Unknown encoder 'xvid'
```
There is no encoder named xvid.  See a list of supported encoders with:
```
ffmpeg -formats
```
You may also need to enable restricted formats:
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)
Hi thank you for the reply, but the thing is PSP cannot handle default mp4 i guess,
because all the videos I can play in PSP are having the following information
ex 1:
Size : 29MB
Length 4'54"
Resolution : 320 x 240
video codec MPEG-4 736 kbps
Audio Codec AAC 64 kbps
Sampling frequency : 24.000 Khz

The Video I converted using your command and placed it in the PSP :

Size : 7432 KB
Length 3'48"
Resolution :-(nothing)
video codec:-
Audio Codec:-
Sampling frequency : -

So can you please tell me how to convert my video, so that it has the properties as in example 1, 

thanks a ton for ur time

---

### Post by FakeOutdoorsman on 2009-11-05
> **vamshi617 said:**
> Hi thank you for the reply, but the thing is PSP cannot handle default mp4 i guess,
because all the videos I can play in PSP are having the following information
ex 1:
Size : 29MB
Length 4'54"
Resolution : 320 x 240
video codec MPEG-4 736 kbps
Audio Codec AAC 64 kbps
Sampling frequency : 24.000 Khz

The Video I converted using your command and placed it in the PSP :

Size : 7432 KB
Length 3'48"
Resolution :-(nothing)
video codec:-
Audio Codec:-
Sampling frequency : -

So can you please tell me how to convert my video, so that it has the properties as in example 1, 

thanks a ton for ur time

Duh... I confused a PSP with a PS 3 in my first post.  Well, that may explain why my suggestion didn't work.  Try this:
```
ffmpeg -i input.flv -acodec copy -vcodec mpeg4 -qscale 5 -s 320x240 output.mp4
```

---

### Post by goldshirt9 on 2009-11-05
can you use 
sony media manager 3 for the psp.
i use in xp but havent tried in linux yet.
i believe the new version will conver for you.

i still use the original version and have no trouble moving movies over to my psp.
it arranges all the movies into the correct files with the image file for you.

i know what a pain the psp can be

---

### Post by NickJones on 2009-11-05
Check out HandBreak. Also, Vixy.net has an online converter that converts Youtube vids and you download them in MP4 format. It is slow as all hell though.

---

### Post by vamshi617 on 2009-11-10
thank you for you time, i havent got a chance to try it, ill let you know once i try it

---

### Post by vamshi617 on 2009-11-10
You were right, tried sony media go and it works great, it takes lot of time converting though, than you :)

---

### Post by jurgen32 on 2009-11-11
I use Avidemux-gtk (just install with in synaptic or in a terminal: sudo apt-get install avidemux)for all kind of formats.
It has a auto function to transcode video to PSP (H.264) and PSP.
I never transcoded to PSP so I'm not sure if this is what you want?

Jurgen

---

