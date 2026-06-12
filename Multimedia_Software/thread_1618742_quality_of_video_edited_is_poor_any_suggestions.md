---
title: "quality of video edited is poor any suggestions"
date: 2010-11-11
forum: Multimedia Software
---

### Post by tapas_mishra on 2010-11-11
I edited some videos via ffmpeg
as follows  (it is a Ubuntu 10.04 64 bit server on an SSH connection)

```
 ffmpeg -i stats_estimation.mp4 -ar 22050 -acodec libmp3lame -ab 32K -r 25  -vcodec flv out2.flv
```Things started perfectly ```

FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1, Copyright (c) 2000-2009
Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1 --prefix=/usr
--enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib
--enable-libgsm --enable-libschroedinger --enable-libspeex
--enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib
--disable-stripping --disable-vhook --enable-runtime-cpudetect
--enable-gpl --enable-postproc --enable-swscale --enable-x11grab
--enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Mar  4 2010 12:41:55, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate:
29.94 (5000/167) -> 44.92 (539/12)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'stats_estimation.mp4':
  Duration: 02:47:05.56, start: 0.000000, bitrate: 237 kb/s
    Stream #0.0(eng): Video: h264, yuv420p, 320x240, 44.92 tbr, 14.97
tbn, 29.94 tbc
    Stream #0.1(eng): Audio: aac, 32000 Hz, stereo, s16
Output #0, flv, to 'out2.flv':
    Stream #0.0(eng): Video: flv, yuv420p, 320x240, q=2-31, 200 kb/s,
90k tbn, 25 tbc
    Stream #0.1(eng): Audio: libmp3lame, 22050 Hz, stereo, s16, 32 kb/s
Stream mapping:
  Stream #0.0 -> #0.0

```but the quality of resulting video is very poor.
What I see is when I enlarge the video there are square marks and
objects in video are blurred.

I had tried using
```
  ffmpeg -i stats_estimation.mp4 -ar 22050 -acodec libmp3lame -ab 32K -r 25  **-s 470x290**  -vcodec flv out2.flv
```thinking as if size might have been the problem but that did not fixed
the issue I get the out put video as poor where as the video (which is
mp4)
is of good quality and no deterioration in its quality when I see the
unconverted video.
ffmpeg is doing some thing which makes the original quality go.
So any suggestions on this part?

---

### Post by FakeOutdoorsman on 2010-11-11
If you don't declare a method of rate control then, by default, FFmpeg will use a value *-b 200k* which is probably too low for you.  Either provide a higher bitrate, or, instead of *-b*, use *-qscale*; such as *-qscale 3*.  The *-sameq* option is often recommended, but this is usually used incorrectly and I hardly ever recommend it.

Secondly, *-vcodec libx264* will provide better results than *-vcodec flv*.  See the [FFmpeg x264 Encoding Guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) for more information and some examples.

---

### Post by tapas_mishra on 2010-11-11
> **FakeOutdoorsman said:**
> If you don't declare a method of rate control then, by default, FFmpeg will use a value *-b 200k* which is probably too low for you.  Either provide a higher bitrate, or, instead of *-b*, use *-qscale*; such as 
I am not a professional video editor so can you tell me what values I can use for bitrate.

---

### Post by FakeOutdoorsman on 2010-11-11
I can't tell you what bitrate or qscale to use because I have no idea of the complexity of your input, and I don't know what type of device the output will be playing on.

If you describe what you are doing or what you want to do with the output video I can attempt to give you an example FFmpeg command.

---

### Post by hugmenot on 2010-11-12
You sure you need flv1? Flash plugin plays H.264 in mp4 just fine.

---

### Post by tapas_mishra on 2010-11-12
> **hugmenot said:**
> You sure you need flv1? Flash plugin plays H.264 in mp4 just fine.

Yes I am sure for flv because mp4 I have ,the problem is I am having a streaming server Red5 where I am doing all this.
Though the docs of Red5 says to support mp4 but when I actually tried it didn't turned out so well.So I decided to stick with flv.

---

### Post by andrew.46 on 2010-11-13
Hi tapas_mishra,

But h.264 video and aac sound will live quite happily in an flv container, I dimly remember giving this command in another thread but here we are:

```

 ffmpeg -i stats_estimation.mp4 -acodec copy -vcodec copy stats_estimation.flv

```

and this will simply alter the container, leaving video and audio unchanged.

Andrew

---

### Post by tapas_mishra on 2010-11-15
I used -sameq as suggested above and every thing works perfectly.
> **andrew.46 said:**
> Hi tapas_mishra,

But h.264 video and aac sound will live quite happily in an flv container, 

Hi,
thanks I am not getting what you meant by above.

May be you would like to give some link or information about above comment so that if some one comes here by chance should help them.

---

### Post by hugmenot on 2010-11-15
[http://en.wikipedia.org/wiki/Flv](http://en.wikipedia.org/wiki/Flv)

Fourth paragraph.

---

