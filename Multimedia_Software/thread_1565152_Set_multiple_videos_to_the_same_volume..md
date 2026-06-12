---
title: "Set multiple videos to the same volume."
date: 2010-08-31
forum: Multimedia Software
---

### Post by VoiDeR on 2010-08-31
I have a bunch of videos that I would like to adjust the volume to be the same on all of them. I have searched and all i can find is how to normalize the volume with in the video. I have tried this and it works great on movies where the action is louder that the talking. My problem is on video is a lot louder than another so im constantly changing the volume when a new video starts.

---

### Post by arrange on 2010-08-31
What programme did you use to adjust the volume?
What is the format of the videos? Ideally, give us the output (see [Terminal](https://help.ubuntu.com/community/GnomeTerminal)) of```
ffmpeg -i the_video.suffix
```

---

### Post by VoiDeR on 2010-08-31
The videos are just mpgs ready to be put on dvd with dvdauthor.

FFmpeg version SVN-r19352-4:0.5+svn20090706-2ubuntu2.2, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5+svn20090706-2ubuntu2.2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --extra-cflags=-I/build/buildd/ffmpeg-0.5+svn20090706/debian/include --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 0 / 52.20. 0
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Apr 23 2010 15:05:49, gcc: 4.4.1

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
Input #0, mpeg, from 'S1E02-Where.No.Man.Has.Gone.Before.mpg':
  Duration: 00:50:25.18, start: 0.241700, bitrate: 2452 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video, yuv420p, 720x480 [PAR 8:9 DAR 4:3], 9800 kb/s, 23.98 tbr, 90k tbn, 47.95 tbc
    Stream #0.1[0x80]: Audio: ac3, 48000 Hz, stereo, s16, 192 kb/s
At least one output file must be specified

---

### Post by VoiDeR on 2010-08-31
Bump

---

### Post by david70 on 2011-05-03
ddvideo video to mp4 gain can set multiple videos or musics to the same volume.adust volume from 75 db to 105 db.very useful.it need to recodec and convert any video to mp4 format with audio normalizer.

---

