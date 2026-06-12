---
title: "Webcam working on xawtv but not with ffmpeg(on kdeinlive)"
date: 2009-10-01
forum: Multimedia Software
---

### Post by TheApe on 2009-10-01
Hi folks!
After almost giving up, I've managed to install my sony vaio webcam(damn sony).

It's the famous r5u870
here is the lsusb result:
```
Bus 001 Device 004: ID 05ca:1830 Ricoh Co., Ltd Visual Communication Camera VGP-VCC2
```

Well, it's working fine with xawtv and gstreamer, but fails to load on cheese. I have already give up trying to use it in cheese, but just in case you guys have any clue ;-)

I need it to work on ffmpeg, since I'm using kdeinlve and it uses ffmpeg to grab video and I don't know any other way to save the input from webcam into a file. Xawtv grabbing is crappy...

It would be great to get it working on kdeinlive, since I have to do some screencasts with video.

Directly on command line I'm trying the following command:
```
$ ffmpeg -f oss -i /dev/dsp -f video4linux2 -i /dev/video0 -s cif /tmp/out.mpg
```

ffmpeg prints this:
```

FFmpeg version git-91be88c, Copyright (c) 2000-2009 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-nonfree --enable-shared --enable-pthreads --enable-libx264 --enable-libfaac --enable-libtheora
  libavutil     50. 3. 0 / 50. 3. 0
  libavcodec    52.32. 0 / 52.20. 0
  libavformat   52.36. 0 / 52.31. 0
  libavdevice   52. 2. 0 / 52. 1. 0
  libswscale     0. 7. 1 /  0. 7. 1
  built on Jul 24 2009 21:22:03, gcc: 4.3.3
Input #0, oss, from '/dev/dsp':
  Duration: N/A, start: 1254442946.179807, bitrate: N/A
    Stream #0.0, 1/1000000: Audio: pcm_s16le, 44100 Hz, mono, s16, 705 kb/s
[video4linux2 @ 0x9e33fd0]Wrong size (0x0)
/dev/video0: Error while opening file

```

do you have any clues?
thanks!!!

---

