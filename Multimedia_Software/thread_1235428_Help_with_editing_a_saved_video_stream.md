---
title: "Help with editing a saved video stream"
date: 2009-08-09
forum: Multimedia Software
---

### Post by acid_crucifix on 2009-08-09
Hey, I've saved a mms video stream using mplayer. Now i want to cut this video and get only a particular part of it as a new video file. But Im not being able to do this. I tried ffmpeg but this was the output
> 
xxxx@Lothlorien:~$ ffmpeg -i convo1.avi -ss 22200 -t 100 convo2.avi
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
[avi @ 0x9845ac0]Could not find codec parameters (Video: wmv3, 352x288)
Input #0, avi, from 'convo1.avi':
  Duration: 00:00:00.00, start: 0.000000, bitrate: -2147483 kb/s
    Stream #0.0: Video: wmv3, 352x288, 1k tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: pcm_s16le, 16000 Hz, stereo, s16, 512 kb/s
File 'convo2.avi' already exists. Overwrite ? [y/N] y
swScaler: Unknown format is not supported as input pixel format
Cannot get resampling context
I do not know what to do to fix this. I tried installing the repo codec files using
> sudo apt-get install libavcodec-dev libavcodec-unstripped-52 libavcodec52 libavdevice-dev libavdevice52 libavfilter-dev libavfilter0 libavformat-dev libavformat52 libavutil49 libpostproc51 libswscale0 but it still doesn't work. Can someone help.

---

### Post by acid_crucifix on 2009-08-09
BUMP

in case my question is unclear.. I used mplayer to save a streaming video. It said that seeking will not be possible. When i open the video in vlc it shows the starting time as 6hrs. I want to cut this video and make a new video with only a particular part of the original vid. 
I tried doing it using ffmpeg using the above command and got the dump as shown. 

If anyone can see a mistake in what ive done or knows any other way to achieve this please help. I need to get this done urgently as its a gift for a friend.

---

### Post by FakeOutdoorsman on 2009-08-09
Your command can be improved in a few ways.  You can place *-ss* and *-t* before declaring the input.  This will let FFmpeg seek directly to your position.  If you place *-ss* and *-t* after the input, then FFmpeg will first decode the video and then seek which will take longer with large files.

You should use the *-acodec copy* and *-vcodec copy* commands, telling FFmpeg to just copy and paste the audio and video streams into a new container (avi in your case) instead of re-encoding everything.

As a personal preference I use the hours:minutes:seconds:frames time format as I find it easier to deal with.  Your final command could look like:
```
ffmpeg -ss 02:15:43:00 -t 00:12:00:00 -i input.avi -acodec copy -vcodec copy output.avi
```

I'm not sure why FFmpeg is giving you the "Could not find codec parameters" error, because FFmpeg should be able to decode wmv3.

---

