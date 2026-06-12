---
title: "Revert ffmpeg or find alternative?"
date: 2010-10-22
forum: Multimedia Software
---

### Post by valros on 2010-10-22
My problem is that ffmpeg that shipped with 10.10 now incorrectly encodes mp3 files, specifically headers are missing at ~0x1481910.

How easy is it to revert ffmpeg to an older version, the last working version being that on Lucid.

An alternative might also be possible, I have already tried having lame re-encode the files and mp3check fix the headers to no avail.

---

### Post by andrew.46 on 2010-10-22
Hi valros,

> **valros said:**
> How easy is it to revert ffmpeg to an older version, the last working version being that on Lucid.

IMHO you would be better to go forward rather than back:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

Can I ask how you see the encoding fault with your current copy of FFmpeg?

Andrew

---

### Post by valros on 2010-10-22
In trying to re-encode the mp3 file with ffmpeg(through winff), the output is:


FFmpeg version 0.6-4:0.6-2ubuntu6, Copyright (c) 2000-2010 the FFmpeg developers
  built on Oct  5 2010 22:36:53 with gcc 4.4.5
  configuration: --extra-version=4:0.6-2ubuntu6 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  WARNING: library configuration mismatch
  libavutil   configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --enable-shared --disable-static
  libavcodec  configuration: --extra-version=4:0.6-2ubuntu3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libdirac --enable-libgsm --enable-libopenjpeg --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-vaapi --enable-pthreads --enable-zlib --enable-libvpx --disable-stripping --enable-runtime-cpudetect --enable-libmp3lame --enable-gpl --enable-postproc --enable-x11grab --enable-libfaad --enable-libxvid --enable-libx264 --enable-librtmp --enable-libdc1394 --enable-shared --disable-static
  libavutil     50.15. 1 / 50.15. 1
  libavcodec    52.72. 2 / 52.72. 2
  libavformat   52.64. 2 / 52.64. 2
  libavdevice   52. 2. 0 / 52. 2. 0
  libavfilter    1.19. 0 /  1.19. 0
  libswscale     0.11. 0 /  0.11. 0
  libpostproc   51. 2. 0 / 51. 2. 0
[mp3 @ 0x12f5640]max_analyze_duration reached
[mp3 @ 0x12f5640]Estimating duration from bitrate, this may be inaccurate
Input #0, mp3, from 'XXX':
  Duration: 00:03:14.87, start: 0.000000, bitrate: 127 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, 2 channels, s16, 128 kb/s
Output #0, mp3, to 'XXX':
  Metadata:
    TSSE            : Lavf52.64.2
    Stream #0.0: Audio: libmp3lame, 44100 Hz, 2 channels, s16, 160 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
Press [q] to stop encoding
[mp3 @ 0x12f6900]Header missing
Error while decoding stream #0.0
[mp3 @ 0x12f6900]overread, skip -7 enddists: -6 -6
[mp3 @ 0x12f6900]overread, skip -5 enddists: -2 -2
[mp3 @ 0x12f6900]overread, skip -5 enddists: -4 -4
size=   10255kB time=525.04 bitrate= 160.0kbits/s    
video:0kB audio:10255kB global headers:0kB muxing overhead 0.000314%
Press Enter to Continue

---

### Post by andrew.46 on 2010-10-23
Hi valros,

I don't suppose you can post the *input* file for that error message somewhere? I would be curious to see if the svn FFmpeg has the same problem, the error seems to suggest a fault with the input:

```

[mp3 @ 0x12f6900]Header missing
Error while **[COLOR="Red"]decoding[/COLOR]** stream #0.0

```

Andrew

---

