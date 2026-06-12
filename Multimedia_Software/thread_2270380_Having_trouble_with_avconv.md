---
title: "Having trouble with avconv"
date: 2015-03-22
forum: Multimedia Software
---

### Post by KenF on 2015-03-22
I know there has to be an easy solution.  I've used ffmpeg in the past, but somehow avconv is giving me problems.  The problem is that avconv drops the audio stream ... and no matter what I do, I can not get audio.

avconv -i whatever.vob out.mp4

Results in a movie with no audio.  When running, it indicates this:

Input #0, mpeg, from 'VTS_08_1.VOB':
  Duration: 00:21:27.13, start: 0.280633, bitrate: 6673 kb/s
    Stream #0.0[0x1e0]: Video: mpeg2video (Main), yuv420p, 720x480 [PAR 32:27 DAR 16:9], 9800 kb/s, 29.97 fps, 29.97 tbr, 90k tbn, 59.94 tbc
    Stream #0.1[0x80]: Audio: ac3, 0 channels
    Stream #0.2[0x82]: Audio: ac3, 0 channels
    Stream #0.3[0x83]: Audio: ac3, 0 channels
    Stream #0.4[0x81]: Audio: ac3, 0 channels
    Stream #0.5[0x84]: Audio: ac3, 0 channels

The audio stream isn't mapped to be encoded:

Stream mapping:
  Stream #0:0 -> #0:0 (mpeg2video -> libx264)
Press ctrl-c to stop encoding


I can't find any successful -map  or -c:a  parameter that picks up any audio stream ... even when I try to get only an audio output.   It must be something simple, but I swear this used to work with ffmpeg (and even with avconv when I used 12.04).

avconv -version gives:

avconv version 9.18-6:9.18-0ubuntu0.14.04.1, Copyright (c) 2000-2014 the Libav developers
  built on Mar 16 2015 13:19:10 with gcc 4.8 (Ubuntu 4.8.2-19ubuntu1)
avconv 9.18-6:9.18-0ubuntu0.14.04.1
libavutil     52.  3. 0 / 52.  3. 0
libavcodec    54. 35. 0 / 54. 35. 0
libavformat   54. 20. 4 / 54. 20. 4
libavdevice   53.  2. 0 / 53.  2. 0
libavfilter    3.  3. 0 /  3.  3. 0
libavresample  1.  0. 1 /  1.  0. 1
libswscale     2.  1. 1 /  2.  1. 1

---

### Post by SeijiSensei on 2015-03-22
```
Audio: ac3, 0 channels
```
That "0 channels" entry looked suspicious so I searched Google for that text string.  There are some threads on the ffmpeg site about problems detecting audio in VOB files.  You might try some of the suggestions in this discussion: [https://trac.ffmpeg.org/ticket/386?cversion=0&cnum_hist=9](https://trac.ffmpeg.org/ticket/386?cversion=0&cnum_hist=9)

I've gone back to ffmpeg using this PPA: [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

---

### Post by KenF on 2015-03-22
Thank you!

This was exactly the problem.   If anyone else has the issue of the sound channels seemingly being ignored, it is because avconv (and ffmpeg) default to gathering that information only at the beginning of the file.

To override the defaults one needs to add:

-analyzeduration 50000000 -probesize 50000000

early in the command line (where 50000000 is some sufficiently large number).

This works for both avconv and ffmpeg (I installed the latter since avconv was not working.  The behavior for both, however, was the same.)

---

