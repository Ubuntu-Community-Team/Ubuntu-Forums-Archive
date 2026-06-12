---
title: "Kdenlive H264 Problem"
date: 2013-01-03
forum: Multimedia Software
---

### Post by GrouchyGaijin on 2013-01-03
Hi Folks,

I'm having a problem with h264 and Kdenlive.

[B]Kdenlive
Version 0.9.2
Using KDE Development Platform 4.8.5 (4.8.5)[/B]

as well as the dev version of ffmpeg.

```

ffmpeg version git-2013-01-02-e4f14c3 Copyright (c) 2000-2013 the FFmpeg developers
  built on Jan  2 2013 18:16:31 with gcc 4.6 (Ubuntu/Linaro 4.6.3-1ubuntu5)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-librtmp --enable-libtheora --enable-libvorbis --enable-libvpx --enable-x11grab --enable-libx264 --enable-nonfree --enable-version3
  libavutil      52. 13.100 / 52. 13.100
  libavcodec     54. 85.100 / 54. 85.100
  libavformat    54. 59.100 / 54. 59.100
  libavdevice    54.  3.102 / 54.  3.102
  libavfilter     3. 30.102 /  3. 30.102
  libswscale      2.  1.103 /  2.  1.103
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100

```
libx264 is set as enabled

I might be misunderstanding [this thread (See the original thread here)]("http://ubuntuforums.org/showthread.php?t=1280510"), but my problem is not audio; it's video. I tried swapping out aac for acodec=libmp3lame and as I thought this didn't affect anything. I can render a file, but when I play it I only hear the audio. I don't see any video.

I've had this problem for a long time, even before I installed the dev version of ffmpeg.

Any ideas on how to solve this?

---

### Post by evilsoup on 2013-01-03
Does encoding a file with libx264 work if you do it directly with ffmpeg on the command-line?

---

### Post by GrouchyGaijin on 2013-01-03
> **evilsoup said:**
> Does encoding a file with libx264 work if you do it directly with ffmpeg on the command-line?
yes it does.
I just ran the following as a test:
```
ffmpeg -i IMG_1770.mov \
       -c:v libx264 -q:v 5 -vf scale=320:-1 \
       -c:a libmp3lame -q:a 3 \
       Mov-to-libx264.flv
```

---

### Post by GrouchyGaijin on 2013-01-08
The problem was the dev version of ffmpeg.  When I downgraded back to the repo version I was able to get everything to work.

---

