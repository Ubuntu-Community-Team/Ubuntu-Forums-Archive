---
title: "Conversion makes things bigger. Loads bigger"
date: 2010-10-28
forum: Multimedia Software
---

### Post by JakeFrederix on 2010-10-28
I've tried using the following command on an .avi file of around 300MB.

```

ffmpeg -i S01E01.avi -target film-dvd output.mov

```The file output.mov reached a size of nearly 600MB before I pulled the plug on it.
Is there a way to keep quality, without making each file huge?

Thanks in advance,
Jake

---

### Post by andrew.46 on 2010-10-28
Hi Jake,

Can I ask what sort of conversion you are trying to do, and the results of the following command:
```

ffmpeg -i S01E01.avi
```

Andrew

---

### Post by mcduck on 2010-10-28
"-target film-dvd" would give you MPEG2 compression, as used on DVD's. That will result in pretty large file. Your original file most likely uses some more modern compression.

Actually depending on what compression your original file uses, you probably don't want to recompress it at all but simply demux it from .avi container into .mov container. Much quicker, and doesn't change the video quality.

---

### Post by JakeFrederix on 2010-10-28
output of ffmpeg -i as requested

```

ffmpeg -i S01E01.avi > output.txt
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:35:30, gcc: 4.4.3
Input #0, avi, from 'S01E01.avi':
  Duration: 00:28:35.69, start: 0.000000, bitrate: 1338 kb/s
    Stream #0.0: Video: mpeg4, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 29.97 tbc
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16, 128 kb/s
At least one output file must be specified


```

---

### Post by andrew.46 on 2010-10-28
Hi Jake,

If you want a mov container then it should be easy as the following codecs:

```

Stream #0.0:**[COLOR="Red"] Video: mpeg4[/COLOR]**, yuv420p, 640x480 [PAR 1:1 DAR 4:3], 29.97 tbr, 29.97 tbn, 29.97 tbc
Stream #0.1: **[COLOR="Red"]Audio: mp3[/COLOR]**, 44100 Hz, stereo, s16, 128 kb/s

```

live quite happily in .mov. As mcduck has suggested a simple demux / remux should do the job:

```
ffmpeg -i S01E01.avi -acodec copy -vcodec copy S01E01.mov
```

Andrew

---

### Post by JakeFrederix on 2010-10-31
```

Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[mov @ 0x98c7ed0]track 1: codec frame size is not set
Could not write header for output file #0 (incorrect codec parameters ?)

```

Is what happens now.

---

