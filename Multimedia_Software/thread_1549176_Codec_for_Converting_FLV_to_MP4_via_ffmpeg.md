---
title: "Codec for Converting FLV to MP4 via ffmpeg"
date: 2010-08-09
forum: Multimedia Software
---

### Post by anjanesh on 2010-08-09
```
ffmpeg -i sample.flv sample.mpg
```Worked - but the mpg quality was much lower and smaller resolution. The input FLV I have is of high quality.

```
ffmpeg -i sample.flv sample.mp4
``````
Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, flv, from 'sample.flv':
  Duration: 00:03:18.34, start: 0.000000, bitrate: 1632 kb/s
    Stream #0.0: Video: vp6f, yuv420p, 940x529, 1536 kb/s, 29.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16, 96 kb/s
Output #0, mp4, to 'sample.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 940x529, q=2-31, 200 kb/s, 90k tbn, 29.92 tbc
    Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1
```Do I need to install a codec ?

---

### Post by ron999 on 2010-08-09
Show the whole printout.

---

### Post by anjanesh on 2010-08-09
```
:~$ ffmpeg -i sample.flv sample.mp4
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.92 (359/12)
Input #0, flv, from 'sample.flv':
  Duration: 00:03:18.34, start: 0.000000, bitrate: 1632 kb/s
    Stream #0.0: Video: vp6f, yuv420p, 940x529, 1536 kb/s, 29.92 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 44100 Hz, stereo, s16, 96 kb/s
Output #0, mp4, to 'sample.mp4':
    Stream #0.0: Video: mpeg4, yuv420p, 940x529, q=2-31, 200 kb/s, 90k tbn, 29.92 tbc
    Stream #0.1: Audio: 0x0000, 44100 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1
```

---

### Post by ron999 on 2010-08-09
OK
In your printout there's a line that says '**configuration -- ..**.....'.
That's where it shows the codecs that are available to ffmpeg.
On that line it needs to say **--enable-libmp3lame**.
Yours doesn't have it.

You should think about rebuilding ffmpeg with the necessary codecs.
There's a tutorial here:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=786095&highlight=Upgrading+FFmpeg+x264")

See, this is my ffmpeg here:-
> FFmpeg version SVN-r24643, Copyright (c) 2000-2010 the FFmpeg developers
  built on Aug  1 2010 10:38:14 with gcc 4.4.1
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-pthreads --enable-libfaac [COLOR="Red"]--enable-libmp3lame[/COLOR] --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab --disable-encoder=vorbis --enable-libvorbis
  libavutil     50.23. 0 / 50.23. 0
  libavcore      0. 2. 0 /  0. 2. 0
  libavcodec    52.84. 2 / 52.84. 2
  libavformat   52.78. 0 / 52.78. 0
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.27. 0 /  1.27. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0


---

### Post by FakeOutdoorsman on 2010-08-09
> **anjanesh said:**
> ```
ffmpeg -i sample.flv sample.mpg
```Worked - but the mpg quality was much lower and smaller resolution.
The default settings for FFmpeg can result in bad quality.  Add a *-qscale 3* to your mpg command and it will look better.  This option tells FFmpeg to encode at a certain quality level instead of encoding video with the default quality option of *-b 200k* which can be quite low depending on the input and the encoder used.

> **ron999 said:**
> You should think about rebuilding ffmpeg with the necessary codecs.

You can still use FFmpeg from the repository instead of compiling.  You will simply have to enable some additional encoders in FFmpeg that Ubuntu turns off by default:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

I prefer compiling though because I can customize FFmpeg how I like and it has some more features and bug fixes than FFmpeg from the repository.  Not everyone needs to compile though (although it's a good learning experience and add to your nerd cred).

MP4 is a container format that can accept several video and audio formats.  There's a good FFmpeg example command called **One-pass CRF** in the link ron999 gave you.  Just remember if you use that example and you are using FFmpeg from the repository, change *-vpre slow* to *-vpre hq* because the repo FFmpeg is too old to have the newer presets (Ubuntu Meerkat's FFmpeg is new enough fortunately).

---

### Post by anjanesh on 2010-08-09
Awesome ! It worked. Thanks.

---

