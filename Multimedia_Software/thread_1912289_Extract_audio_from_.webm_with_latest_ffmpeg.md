---
title: "Extract audio from .webm with latest ffmpeg?"
date: 2012-01-20
forum: Multimedia Software
---

### Post by doubi on 2012-01-20
Hi all,

Am running the following command:
```

$:~$ ffmpeg -i ./input.webm -strict experimental -acodec vorbis -ab 128k -vn ./output.ogg
ffmpeg version N-36951-g48706f4 Copyright (c) 2000-2012 the FFmpeg developers
  built on Jan 20 2012 13:35:09 with gcc 4.4.3
  configuration: --prefix=/usr --enable-avfilter --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil      51. 34.101 / 51. 34.101
  libavcodec     53. 57.105 / 53. 57.105
  libavformat    53. 30.100 / 53. 30.100
  libavdevice    53.  4.100 / 53.  4.100
  libavfilter     2. 59.101 /  2. 59.101
  libswscale      2.  1.100 /  2.  1.100
  libswresample   0.  6.100 /  0.  6.100
  libpostproc    52.  0.100 / 52.  0.100
Input #0, matroska,webm, from './input.webm':
  Duration: 00:01:58.35, start: 0.000000, bitrate: 158 kb/s
    Stream #0:0: Video: vp8, yuv420p, 540x360, SAR 1:1 DAR 3:2, 29.97 fps, 59.94 tbr, 1k tbn, 1k tbc (default)
    Stream #0:1: Audio: vorbis, 44100 Hz, stereo, s16 (default)
Output #0, ogg, to './output.ogg':
  Metadata:
    encoder         : Lavf53.30.100
    Stream #0:0: Audio: vorbis, 44100 Hz, stereo, s16, 128 kb/s (default)
Stream mapping:
  Stream #0:1 -> #0:0 (vorbis -> vorbis)
Press [q] to stop, [?] for help
size=     274kB time=00:01:58.11 bitrate=  19.0kbits/s    
video:0kB audio:265kB global headers:3kB muxing overhead 2.087309%
$

```That's all the output. The output file created is the right length of audio (1:58, as long as the video) but is completely silent.

As you can see, I'm running the latest ffmpeg, git-cloned and compiled today.

Any idea what I'm missing here?

---

### Post by ron999 on 2012-01-20
> **doubi said:**
> 
Any idea what I'm missing here?
Hi
Try this:-
```
ffmpeg -i ./input.webm -vn -acodec copy ./output.ogg
```

---

### Post by doubi on 2012-01-20
> **ron999 said:**
> Hi
Try this:-
```
ffmpeg -i ./input.webm -vn -acodec copy ./output.ogg
```
Outstanding! And it didn't even need the `-strict experimental` flag for some reason.

I'm sure that trick'll help me out more in future. Many thanks ron999!

---

