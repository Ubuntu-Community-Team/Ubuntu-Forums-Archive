---
title: "winff/ffmpeg problem"
date: 2012-01-27
forum: Multimedia Software
---

### Post by masterrob213 on 2012-01-27
I try to convert any file and i get 
FFmpeg version SVN-r0.5.1-4:0.5.1-1ubuntu1.3, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --extra-version=4:0.5.1-1ubuntu1.3 --prefix=/usr --enable-avfilter --enable-avfilter-lavf --enable-vdpau --enable-bzlib --enable-libgsm --enable-libschroedinger --enable-libspeex --enable-libtheora --enable-libvorbis --enable-pthreads --enable-zlib --disable-stripping --disable-vhook --enable-runtime-cpudetect --enable-gpl --enable-postproc --enable-swscale --enable-x11grab --enable-libdc1394 --enable-shared --disable-static
  libavutil     49.15. 0 / 49.15. 0
  libavcodec    52.20. 1 / 52.20. 1
  libavformat   52.31. 0 / 52.31. 0
  libavdevice   52. 1. 0 / 52. 1. 0
  libavfilter    0. 4. 0 /  0. 4. 0
  libswscale     0. 7. 1 /  0. 7. 1
  libpostproc   51. 2. 0 / 51. 2. 0
  built on Dec 21 2011 18:37:21, gcc: 4.4.3

Seems stream 0 codec frame rate differs from container frame rate: 47.95 (48000/1001) -> 23.98 (24000/1001)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from '/home/masterrob213/Desktop/Coming Soon.failed-conv.mp4':
  Duration: 00:00:09.05, start: 0.000000, bitrate: 367 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 640x360, 23.98 tbr, 23.98 tbn, 47.95 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16
Unknown encoder 'libmp3lame'

and i get no file or anything so how can i fix this?

---

### Post by andrew.46 on 2012-01-27
I suspect you have a version of FFmpeg that has been crippled by the packagers. Have a look here for a possible solution:

HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg
[http://ubuntuforums.org/showthread.php?t=1117283](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by masterrob213 on 2012-01-28
that helped thank you :) i tried it again and now instead of that i get unknown encoder 'libfaac'







ok i fexed that problem now i get 
Seems stream 0 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 24.00 (24/1)
Input #0, flv, from '/home/masterrob213/Desktop/Final Fantasy VII Advent Children Movie.flv':
  Duration: 01:11:50.81, start: 0.000000, bitrate: 270 kb/s
    Stream #0.0: Video: flv, yuv420p, 400x218, 262 kb/s, 24 tbr, 1k tbn, 1k tbc
    Stream #0.1: Audio: mp3, 22050 Hz, stereo, s16, 8 kb/s
Output #0, 3gp, to '/home/masterrob213/Final Fantasy VII Advent Children Movie.3gp':
    Stream #0.0: Video: libx264, yuv420p, 320x240, q=2-31, 128 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: libfaac, 22050 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libx264 @ 0x91327c0]broken ffmpeg default settings detected
[libx264 @ 0x91327c0]use an encoding preset (vpre)
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

---

### Post by FakeOutdoorsman on 2012-01-28
You'll need to follow **Option C** from the link Andrew provided.

---

### Post by masterrob213 on 2012-01-29
Output #0, 3gp, to '/home/masterrob213/Final Fantasy VII Advent Children Movie.3gp':
    Stream #0.0: Video: libx264, yuv420p, 320x240, q=2-31, 128 kb/s, 90k tbn, 15 tbc
    Stream #0.1: Audio: libfaac, 22050 Hz, stereo, s16, 64 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
[libx264 @ 0x866dd40]broken ffmpeg default settings detected
[libx264 @ 0x866dd40]use an encoding preset (vpre)
Error while opening codec for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

Still same problem

---

### Post by FakeOutdoorsman on 2012-01-29
What "Convert To..." and "Device Preset" did you choose in WinFF? Are you using Ubuntu Lucid?

---

### Post by masterrob213 on 2012-01-29
convert to moble phone device preset 3GPP H.264 320x240 4:3 AAC stereo

yes i am useing ubuntu lucid

---

### Post by FakeOutdoorsman on 2012-01-30
I don't have that "Device Preset" in WinFF from the repository so I can't see what the exact problem is, but your version of FFmpeg most likely uses a different syntax than what your version of WinFF uses and gives you the *broken ffmpeg default settings detected* message.

You can use ffmpeg directly instead:
```
ffmpeg -i input -s 320x240 -vcodec libx264 -vpre normal -vpre baseline -crf 28 -acodec libfaac -ab 64k -ac 2 -threads 0 output.3gp
```

Or someone more familiar with WinFF may be able to direct you to proper WinFF presets.

---

