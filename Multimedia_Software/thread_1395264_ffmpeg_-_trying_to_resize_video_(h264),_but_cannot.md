---
title: "ffmpeg - trying to resize video (h264), but cannot?"
date: 2010-01-31
forum: Multimedia Software
---

### Post by rdeleonp on 2010-01-31
Hi, all.

On Ubuntu 9.10, I'm trying to resize a video I downloaded from YouTube using ffmpeg.

The problem is, I cannot seem to be able to resize the video. The output resolution is always the same as the input resolution:

```

rdl@newage:/tmp$ uname -a
Linux newage 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

rdl@newage:/tmp$ ffmpeg -i video.mp4 
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

Seems stream 1 codec frame rate differs from container frame rate: 49.04 (49042/1000) -> 24.50 (49/2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'video.mp4':
  Duration: 00:01:10.93, start: 0.000000, bitrate: 2116 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 1280x720, 24.50 tbr, 24.52 tbn, 49.04 tbc
At least one output file must be specified

rdl@newage:/tmp$ ffmpeg -vtag DIVX -b 4000k -ab 160k -s 640x350 -i video.mp4 video.avi
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

Seems stream 1 codec frame rate differs from container frame rate: 49.04 (49042/1000) -> 24.50 (49/2)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'video.mp4':
  Duration: 00:01:10.93, start: 0.000000, bitrate: 2116 kb/s
    Stream #0.0(und): Audio: aac, 44100 Hz, stereo, s16
    Stream #0.1(und): Video: h264, yuv420p, 1280x720, 24.50 tbr, 24.52 tbn, 49.04 tbc
Output #0, avi, to 'video.avi':
    Stream #0.0(und): Video: mpeg4, yuv420p, 1280x720, q=2-31, 4000 kb/s, 90k tbn, 24.50 tbc
    Stream #0.1(und): Audio: mp2, 44100 Hz, stereo, s16, 160 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Press [q] to stop encoding
frame= 1727 fps= 27 q=2.0 Lsize=   33975kB time=70.53 bitrate=3946.2kbits/s    
video:32475kB audio:1385kB global headers:0kB muxing overhead 0.342051%

```Can anyone spot what I'm doing wrong?

Thanks a lot.

---

### Post by Jose Catre-Vandis on 2010-01-31
Its something to do with the order of parameters you are using. if you try a command like:

```
ffmpeg -i input.mp4 -s 640x360 -b 4000k -ab 160k -vtag DIVX output.avi
```

You should get the result you are after. Build up from there. Oh. a height of 350 may not work (needs to be even and/or divisible by 4, but given your input is 1280x720, if you choose a width of 640 then the height should be 360?)

or you may want to add some padding left and right to prevent distortion

e.g -padleft n  -padright n

---

### Post by rdeleonp on 2010-01-31
That did the trick. Thanks a lot!

---

