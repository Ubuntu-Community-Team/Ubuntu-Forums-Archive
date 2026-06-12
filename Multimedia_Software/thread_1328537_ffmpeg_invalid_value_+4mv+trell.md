---
title: "ffmpeg invalid value +4mv+trell"
date: 2009-11-16
forum: Multimedia Software
---

### Post by Ladgalen on 2009-11-16
Hi

I would like to convert avi video into mp4 video in order to read them on my ipod.

I used that command

```
ffmpeg -i nomvideo.avi -acodec aac -ab 128kb -vcodec mpeg4 -b 1200kb -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 320x180 -title X nomvideo.mp4
```

But I had got that error message :
```

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
[NULL @ 0x92f3580]Invalid and inefficient vfw-avi packed B frames detected
Input #0, avi, from 'nomvideo.avi':
  Duration: 01:49:18.28, start: 0.000000, bitrate: 895 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 576x320 [PAR 1:1 DAR 9:5], 25 tbr, 25 tbn, 25 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
Unable to parse option value "trell": undefined constant or missing (
Invalid value '+4mv+trell' for option 'flags'

```

Have you got any idea or solution for me ?

Thanks

---

### Post by FakeOutdoorsman on 2009-11-16
Your command is designed for older FFmpeg.  An equivalent for more recent FFmpeg:
```
ffmpeg -i nomvideo.avi -acodec aac -ab 128k -vcodec mpeg4 -b 1200k -mbd 2 -flags +mv4+aic -trellis 1 -cmp 2 -subcmp 2 -s 320x180 -metadata title=X nomvideo.mp4
```

Unfortunately, encoding to AAC audio is unavailable for Ubuntu Karmic FFmpeg due to licensing issues.  Maybe mp3 audio works with iPood in a mp4 container:
```
ffmpeg -i nomvideo.avi -acodec libmp3lame -ab 128k -vcodec mpeg4 -b 1200k -mbd 2 -flags +mv4+aic -trellis 1 -cmp 2 -subcmp 2 -s 320x180 -metadata title=X nomvideo.mp4
```

Another option is to compile FFmpeg yourself and use the iPod presets.  It will look better than the above commands.  Instructions and iPod encoding example:
[url=http://ubuntuforums.org/showthread.php?t=786095]
HOWTO: Install and use the latest FFmpeg and x264[/url]

---

