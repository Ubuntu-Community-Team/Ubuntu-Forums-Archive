---
title: "MP3 seek failure"
date: 2013-02-06
forum: Multimedia Software
---

### Post by reevery on 2013-02-06
Hi

I have been working through the thread [http://ubuntuforums.org/showthread.php?t=2002722](http://ubuntuforums.org/showthread.php?t=2002722) but as it's been six months thought it better to start afresh.

I've hit a problem with my encoder, that mp3 files made with it (ffmpeg --libmp3lame) do not allow seeking. It's definitely an encoder fault - the problem is replicated with various players, and with the players files encoded elsewhere work. I have tried all of the solutions on the thread above.

I have successfully encoded the mp3s using a different machine, but it's where my web hosting is and is not really a convenient solution.

The encoder there has highlighted some differences:
```
Input #0, mp3, from 'infile.mp3':
  Metadata:
    encoder         : Lavf53.21.0
  Duration: 01:01:57.69, start: 0.000000, bitrate: 192 kb/s
    Stream #0.0: Audio: mp3, 44100 Hz, stereo, s16, 192 kb/s
Output #0, mp3, to 'tmp.mp3':
  Metadata:
    TSSE            : Lavf53.2.0
    Stream #0.0: Audio: libmp3lame, 44100 Hz, stereo, s16, 192 kb/s
```
So I guess the problem is with Lavf53. I'd like to roll back the version on my local machine to Lavf53.2.0, and see if that solves the problem, but a quick Google with that as a keyword has led to a number of bug reports and I cannot find how I can roll back.

So I have two questions:
1) How can I change the lavf53 version?
2) Is the encoder / TSSE difference relevant?

Thank you for your assistance.

---

### Post by andrew.46 on 2013-02-06
Perhaps update to latest git FFmpeg, this carries 54. 61.104...

---

### Post by FakeOutdoorsman on 2013-02-07
It makes more sense to use something newer instead of older due to the high development activity in FFmpeg which gives a good chance of your bug being fixed. The only time you will want to use an older version for general usage is if you found a regression in the latest code. You can try a static build via the [FFmpeg download](http://ffmpeg.org/download.html#LinuxBuilds) page for a quick test without needing to compile.

---

### Post by reevery on 2013-02-11
Thank you. I installed the [Jon Severinsson PPA]("https://launchpad.net/~jon-severinsson/+archive/ffmpeg") and this has done the trick. Thank you for pointing me in the right direction.

---

