---
title: "ffmpeg question"
date: 2009-12-17
forum: Multimedia Software
---

### Post by 8Kuula on 2009-12-17
Im trying to remove black bars from video and remove subtitles.
ffmpeg -i video.mkv -map 0:0 -map 0:1 -vcodec copy -croptop 92 -cropbottom 92 -acodec copy cropvideo.mkv
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
  built on Oct 13 2009 22:35:00, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (54042/1127) -> 23.98 (24000/1001)
Input #0, matroska, from 'Video.mkv':
  Duration: 02:05:53.58, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264, yuv420p, 1280x720, PAR 1:1 DAR 16:9, 23.98 tbr, 1k tbn, 47.95 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, s16
    Stream #0.2: Subtitle: 0x0000
    Stream #0.3: Subtitle: 0x0000
    Stream #0.4: Subtitle: 0x0000
    Stream #0.5: Subtitle: 0x0000
Number of stream maps must match number of output streams

```

What im doing wrong? :I

---

### Post by mc4man on 2009-12-17
Maybe add a -sn to command
Never had reason to crop, but I'd think you'd need to re-encode to actually do so, at best I'd think your just affecting the aspect ratio (depending on player

---

### Post by 8Kuula on 2009-12-18
Thanks, that worked, kinda :)
```
[NULL @ 0x17b6080]error, non monotone timestamps 167 >= 42
av_interleaved_write_frame(): Error while opening file
```

Now it gives this. But seems easier just to let it be, only did hope get little smaller file.

Those black bars in video file take some ammounnt of data (I think), image is 1280x720 instead 1280x536 and video player puts those black bars anyways to 1280x536 resolution video, so wasted data in video file.

"Trying is the first step to failure" :D

---

### Post by VertexPusher on 2009-12-18
Removing black bars requires re-encoding, i.e. "-vcodec copy" won't work.

Removing subtitles from MKV files may be easier using mkvtoolnix.

---

