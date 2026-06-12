---
title: "h264 video files playback problems, HELP PLEASE."
date: 2011-03-02
forum: Multimedia Software
---

### Post by MWesten on 2011-03-02
Hello friends, **I'm having issues with h264 video files**, I have a sony HD camcorder and the video files have .MTS extension, so when I try to play the files, they play but very slow.

I  realized about this because** I was about to edit one of those files  with OpenShot and in the preview the video plays very very slow.**

[B]If  I open the video using ffplay MyVideo.MTS  it plays slow too and with melt MyVideo.MTS is also the same.
[/B]
**When I type ffmpeg -i MyVideo.MTS I get this:**

```
ffmpeg -i  00117.MTS
FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:35:47 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavformat configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavdevice configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavfilter configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libswscale  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libpostproc configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --shlibdir=/usr/lib/i686/cmov --cpu=i686 --enable-shared --disable-static --disable-ffmpeg --disable-ffplay
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 59.94 (60000/1001)
Input #0, mpegts, from '00117.MTS':
  Duration: 00:01:29.12, start: 1.000033, bitrate: 17322 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 59.96 fps, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1100]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
    Stream #0.2[0x1200]: Subtitle: pgssub
At least one output file must be specified

```I don't know what to do, is there something I need to install or remove to fix this? A package, some codec? Please help me.

Thanks in advance and I'll be waiting for your kind answer.

Michael

[COLOR=Red]_**EDIT: I tried [this guide]("http://ubuntuforums.org/showthread.php?t=786095") but the issue is still happening, but now when I type ffmpeg -i MyVideo.MTS I get a different output, this is what I get now:**_

[COLOR=Black]```
 ffmpeg -i  00117.MTS
FFmpeg version git-8cf9a09, Copyright (c) 2000-2011 the FFmpeg developers
  built on Mar  2 2011 17:19:11 with gcc 4.4.5
  configuration: --enable-gpl --enable-version3 --enable-nonfree --enable-postproc --enable-libfaac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-libxvid --enable-x11grab
  libavutil    50. 39. 0 / 50. 39. 0
  libavcodec   52.113. 2 / 52.113. 2
  libavformat  52.102. 0 / 52.102. 0
  libavdevice  52.  2. 3 / 52.  2. 3
  libavfilter   1. 76. 0 /  1. 76. 0
  libswscale    0. 12. 0 /  0. 12. 0
  libpostproc  51.  2. 0 / 51.  2. 0

Seems stream 0 codec frame rate differs from container frame rate: 59.94 (60000/1001) -> 59.94 (60000/1001)
Input #0, mpegts, from '00117.MTS':
  Duration: 00:01:29.12, start: 1.000033, bitrate: 17322 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264 (High), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 59.96 fps, 59.94 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x1100]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
    Stream #0.2[0x1200]: Subtitle: pgssub
At least one output file must be specified

```
[/COLOR][/COLOR]

---

### Post by FakeOutdoorsman on 2011-03-02
That video is 1920x1080 and your computer may not be able to decode it at a fast enough speed. If you have a video card that can support hardware accelerated decoding you may be able to view it normally, but you will have to recompile FFmpeg with some additional dependencies.

---

### Post by MWesten on 2011-03-02
FakeOutdoorsman thanks a lof for your answer. Could it be something with Ubuntu 10.10 ? I remember to play this videos on Ubuntu 10.04 and everything went ok, no slow playing.

Another question is: How do I  recompile FFmpeg with some additional dependencies?

Thanks again!!!

---

### Post by FakeOutdoorsman on 2011-03-02
I saw "FFmpeg version 0.6-4:0.6-2ubuntu6" and for some reason thought you were using 10.04, but that's a 10.10 package. If you followed the guide you linked to then your FFmpeg should already be setup to work with your graphics card (assuming it supports VDPAU or whatever).

Does it also play slowly with *ffplay*?
```
ffplay 00117.MTS
```

---

### Post by MWesten on 2011-03-03
FakeOutdoorsman, thanks again.
Yes, I use Ubuntu 10.10 and when I use ffplay MyVideo.MTS the same issue happens.

I followed the guide I linked but same issue is happening, the only thing is that the WARNING I was getting when I typed ffmpeg -i MyVideo.MTS disappeared after what I did (the steps on the guide).

Do you have any idea about how to fix this?

I really appreciate your help.

Thanks.

Michael

---

### Post by FakeOutdoorsman on 2011-03-03
So these same videos played smoothly using the same hardware on 10.04, but not with 10.10?

As for the WARNING you don't need to worry about that. It's just the way the repository FFmpeg was configured, but it won't affect usage.

---

### Post by MWesten on 2011-03-03
Yes, the same videos played good on 10.04.
Could it be that I didn't make a clean 10.10 installation? I upgraded from 10.04.

I even made a backup image of my system using Remastersys so I don't have to reinstall every app when I install Ubuntu in another machine.

I'm just trying to find out what is going on as I wouldn't like to install Ubuntu 10.10 again from zero.

Thanks again and I appreciate any idea you might have.

Michael

---

### Post by BicyclerBoy on 2011-03-03
I'm no expert..just an idea..
Your first compiled ffmpeg was configured with -enable-shared & not with enable-nonfree.

The shared bit could make the ubuntu shared lib packages get overwritten ??
The missing non-free bit leaves stuff out.
Not sure cos I have never tried those options..
But that would screw up all your other package manager installed apps.

Your second compiled ffmpeg (git) seems configured okay..(not that I'm very sure).

Maybe you should make sure your shared system libs (avformat, avcodec etc) are reinstalled from medibuntu & not your build attempts.

ffplay is a bit unreliable. VLC is a better bet to check playback speed.

---

### Post by MWesten on 2011-03-03
BicyclerBoy, thanks for your replay, can you please tell me how do I make sure my  shared system libs (avformat, avcodec  etc) are reinstalled from medibuntu?

Thanks a lot!!!!

---

### Post by FakeOutdoorsman on 2011-03-03
> **BicyclerBoy said:**
> I'm no expert..just an idea..
Your first compiled ffmpeg was configured with -enable-shared & not with enable-nonfree.
He was using FFmpeg from the repository.

> **BicyclerBoy said:**
> The shared bit could make the ubuntu shared lib packages get overwritten ??
The missing non-free bit leaves stuff out.
*--enable-nonfree* will not provide anything that is required to decode this input.

> **BicyclerBoy said:**
> ffplay is a bit unreliable. VLC is a better bet to check playback speed.
What is unreliable about ffplay?

---

### Post by BicyclerBoy on 2011-03-04
@OP ignore everything I said..
Didn't realise the first ffmpeg was repo.
Might be worth trying Ubuntu repo ffmpeg & medibuntu versions of libav*..


ffplay is called unreliable on the ffmpeg forums by the devs...

---

