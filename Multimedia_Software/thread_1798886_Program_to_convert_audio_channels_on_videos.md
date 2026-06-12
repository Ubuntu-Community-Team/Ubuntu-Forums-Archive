---
title: "Program to convert audio channels on videos"
date: 2011-07-06
forum: Multimedia Software
---

### Post by cheesekiller on 2011-07-06
I have a need to convert mp4 files with 5.1 surround to 2 channel audio (or atleast some other format and retain the 1080p resolution) but I need to know what program would be good to use.....   Does anyone have any suggestions? I tried winff to convert file format but it had an error because of the audio being 5.1 (i guess)... meh

---

### Post by cheesekiller on 2011-07-07
bump?

---

### Post by andrew.46 on 2011-07-08
> **cheesekiller said:**
>  I tried winff to convert file format but it had an error because of the audio being 5.1 (i guess)... meh

Can I ask what the error was?

---

### Post by cheesekiller on 2011-07-08
```
FFmpeg version 0.6.2-4:0.6.2-1ubuntu1, Copyright (c) 2000-2010 the Libav developers
  built on Mar 22 2011 15:55:04 with gcc 4.5.2
  configuration: --extra-version=4:0.6.2-1ubuntu1 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavformat configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libswscale  configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libpostproc configuration: --extra-version=4:0.6.2-1ubuntu2 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-vaapi --enable-libopenjpeg --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libfaad --enable-libdirac --enable-libfaad --enable-libmp3lame --enable-librtmp --enable-libx264 --enable-libxvid --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (5000000/104271) -> 23.98 (24000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/matt/Public/2011ExpoCenterPaleriderDIDit.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 1
    compatible_brands: isomavc1
  Duration: 02:58:25.11, start: 0.000000, bitrate: 3209 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 1920x800 [PAR 1:1 DAR 12:5], 2804 kb/s, 23.98 fps, 23.98 tbr, 24k tbn, 47.95 tbc
    Stream #0.1(eng): Audio: aac, 48000 Hz, 5.1, s16, 402 kb/s
Output #0, avi, to '/home/matt/2011ExpoCenterPaleriderDIDit.avi':
  Metadata:
    ISFT            : Lavf52.64.2
    Stream #0.0(und): Video: mpeg4 (hq), yuv420p, 704x384 [PAR 32:33 DAR 16:9], q=3-5, 1500 kb/s, 29.97 tbn, 29.97 tbc
    Stream #0.1(eng): Audio: libmp3lame, 48000 Hz, 2 channels, s16, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press [q] to stop encoding
Resampling with input channels greater than 2 unsupported.
Can not resample 6 channels @ 48000 Hz to 2 channels @ 48000 Hz
Press Enter to Continue

```

---

### Post by andrew.46 on 2011-07-08
So this is the problem:

```

Resampling with input channels greater than 2 unsupported.
Can not resample 6 channels @ 48000 Hz to 2 channels @ 48000 Hz

```

Good news is that this is no longer unsupported with FFmpeg as of [May 23rd 2011]("http://git.videolan.org/?p=ffmpeg.git;a=commit;h=02260ccc3b7f8b88c11af4739252f5c5f97fa6e7"). If you are keen you can upgrade your copy by following this great guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

and then perhaps you will need to use the[ more recent presets for winFF]("http://ubuntuforums.org/showpost.php?p=10871050&postcount=1747").

---

