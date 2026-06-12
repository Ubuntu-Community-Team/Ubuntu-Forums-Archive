---
title: "Converting .avi to .mp4"
date: 2009-12-28
forum: Multimedia Software
---

### Post by arashiko28 on 2009-12-28
I'm looking either way to compress some videos to a desired size, trying just to resize it on avidemux I get only a 2-3 MB less and a very past audio while no changes on video.

I tried to change from avi to mp4 using ffmpeg, this is the result.

>  ffmpeg -i Itazura\ Na\ Kiss\ -\ 01.avi itazura-01.mp4
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:35:00, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from 'Itazura Na Kiss - 01.avi':
  Duration: 00:23:59.98, start: 0.000000, bitrate: 1052 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 704x396 [PAR 1:1 DAR 16:9], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 192 kb/s
Output #0, mp4, to 'itazura-01.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 704x396 [PAR 1:1 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 23.98 tbc
    Stream #0.1: Audio: 0x0000, 48000 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1


How can I successfully pass it from avi to mp4 with perhaps a 20-30 mb drop on the size. (from 108 to 150mb).
Or just keep it avi with the resize?

---

### Post by Shrek01 on 2009-12-28
Ffmpeg doesn't know the audio codec.

Do you have libmp3lame0 installed?
```
sudo dpkg -l libmp3lame0
```If or when you do, add to your ffmpeg line -acodec libmp3lame 

```
ffmpeg -i Itazura\ Na\ Kiss\ -\ 01.avi -acodec libmp3lame itazura-01.mp4
```

---

### Post by arashiko28 on 2009-12-28
Yes I do have it, but there an error message:

> ffmpeg -i Itazura\ Na\ Kiss\ -\ 01.avi -acodec libmp3lame itazura-01.mp4
FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Oct 13 2009 22:35:00, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997/125)
Input #0, avi, from 'Itazura Na Kiss - 01.avi':
  Duration: 00:23:59.98, start: 0.000000, bitrate: 1052 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 704x396 [PAR 1:1 DAR 16:9], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 192 kb/s
Unknown encoder 'libmp3lame'


---

### Post by arashiko28 on 2009-12-28
Right now I'm more interested into dropping a couple of megabites without something like the chipmunks high on caffeine for audio.

---

### Post by FakeOutdoorsman on 2009-12-28
You need to enable the restricted encoders in FFmpeg.  Follow either option A or option C in the following link:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Once you enable these encoders in FFmpeg you can try one of the encoding examples (I recommend the one-pass CRF example) shown here:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

Also, you can remove **libmp3lame0**.  FFmpeg won't use that package.

---

