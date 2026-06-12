---
title: "FFMPEG: Invalid pixel aspect ratio"
date: 2015-06-17
forum: Multimedia Software
---

### Post by alfirdaous on 2015-06-17
Hello everybody,

I tried to run a FFMPEG command line, and it results to this error:

```

[mpeg4 @ 0x639b80] Invalid pixel aspect ratio 640/639, limit is 255/255

```

the full code and error:

```

ffmpeg -i INPUT.mp4 -strict experimental -vf "delogo=x=20:y=350:w=100:h=100:band=100:show=1" OUTPUT.mp4
ffmpeg version 0.8.17-4:0.8.17-0ubuntu0.12.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Mar 16 2015 13:26:50 with gcc 4.6.3
The ffmpeg program is only provided for script compatibility and will be removed
in a future release. It has been deprecated in the Libav project to allow for
incompatible command line syntax improvements in its replacement called avconv
(see Changelog for details). Please use avconv instead.
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'INPUT.mp4':
  Metadata:
    major_brand     : isom
    minor_version   : 512
    compatible_brands: isomiso2avc1mp41
    title           : 885170921547744
    encoder         : Lavf56.4.101
  Duration: 00:01:08.49, start: 0.161134, bitrate: 149 kb/s
    Stream #0.0(und): Video: h264 (Main), yuv420p, 426x240 [PAR 640:639 DAR 16:9], 96 kb/s, 25 fps, 25 tbr, 12800 tbn, 50 tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, 2 channels (FC), s16, 48 kb/s
File 'OUTPUT.mp4' already exists. Overwrite ? [y/N] y
[buffer @ 0x6469c0] w:426 h:240 pixfmt:yuv420p
[mpeg4 @ 0x639b80] Invalid pixel aspect ratio 640/639, limit is 255/255
Output #0, mp4, to 'OUTPUT.mp4':
    Stream #0.0(und): Video: mpeg4, yuv420p, 426x240 [PAR 640:639 DAR 16:9], q=2-31, 200 kb/s, 90k tbn, 25 tbc
    Stream #0.1(und): Audio: libvo_aacenc, 44100 Hz, 2 channels, s16, 200 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height

```

Thanks in advance

---

### Post by FakeOutdoorsman on 2015-06-20
You're using the old, buggy, dead, counterfeit "ffmpeg" from Libav, a fork of the FFmpeg project.

Download a [static build of the real ffmpeg](http://johnvansickle.com/ffmpeg/). It should work unlike the impostor.

Many thanks to the maintainer who thought this mess was a great idea.

---

### Post by alfirdaous on 2015-06-25
Thanks man I will check that

---

