---
title: "Video conversion error"
date: 2010-05-08
forum: Multimedia Software
---

### Post by arnab_das on 2010-05-08
I am currently using nokia n97, which supports no other video formats other than 3gp and mp4.

i have searched across various threads but have as of now found no solution regarding mp4 conversion.

here's what i get when i try converting an avi file to mp4:

```
~$ ffmpeg -i video.avi -b 2300k -r 30 -s 640x360 N97movie.mp4
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
[NULL @ 0xa4a260]Invalid and inefficient vfw-avi packed B frames detected

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from 'video.avi':
  Duration: 00:02:55.35, start: 0.000000, bitrate: 2775 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 192 kb/s
Output #0, mp4, to 'N97movie.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 640x360 [PAR 3:4 DAR 4:3], q=2-31, 2300 kb/s, 90k tbn, 30 tbc
    Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1

```

---

### Post by arnab_das on 2010-05-08
I did try out winff as well, but here's the error message it gives me:

```
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:38:06, gcc: 4.4.1
[NULL @ 0x1f63270]Invalid and inefficient vfw-avi packed B frames detected

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from '/home/arnab/video.avi':
  Duration: 00:02:55.35, start: 0.000000, bitrate: 2775 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 192 kb/s
Unknown encoder 'libfaac'
Press Enter to Continue

```

---

### Post by lisati on 2010-05-08
Moved to "Multimedia and video"

---

### Post by andrew.46 on 2010-05-08
Hi arnab_das,

I suspect the default settings are steering you towards aac sound for your output file. Have a look here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and I suspect if you follow the directions there you should be right.

All the best,

Andrew

---

### Post by arnab_das on 2010-05-09
> **andrew.46 said:**
> Hi arnab_das,

I suspect the default settings are steering you towards aac sound for your output file. Have a look here:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

and I suspect if you follow the directions there you should be right.

All the best,

Andrew

installing the medibuntu repositories solved it. thanks for the help. a question though. how's the medibuntu repos different from the restricted extras?

---

### Post by andrew.46 on 2010-05-09
Hi arnab,

> **arnab_das said:**
> installing the medibuntu repositories solved it. thanks for the help. a question though. how's the medibuntu repos different from the restricted extras?

Good to hear the issue is resolved :). Often the installation of the '[restricted extras]("http://packages.ubuntu.com/karmic/ubuntu-restricted-extras")' is suggested as a cure for almost every media problem under Ubuntu, and I sometimes wonder if everybody who suggests this meta package is fully aware of its contents. In this case the restricted extras installs a copy of libavcodec that has been deliberately stripped of the ability to encode to aac by the Ubuntu developers. In response to this Medibuntu, which has no 'official' connection to Ubuntu, has been good enough to create a package called [libavcodec-extra-52]("http://packages.medibuntu.org/karmic/libavcodec-extra-52.html") which amongst other things allows FFmpeg to transcode to aac. And this of course solved your dilemma :). 

All the best,

Andrew

---

