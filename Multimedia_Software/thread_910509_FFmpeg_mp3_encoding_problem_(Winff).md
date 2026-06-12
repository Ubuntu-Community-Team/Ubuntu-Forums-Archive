---
title: "FFmpeg mp3 encoding problem (Winff)"
date: 2008-09-04
forum: Multimedia Software
---

### Post by RageAgainstThis on 2008-09-04
I am trying to convert some videos to my sansa player.  The destination format is mpg (mpeg2 mp3).  It looks as though my video codec is working but ffmpeg cannot find a suitable codec for mp3.  I have installed the ffmpeg from medibuntu repositories and latest winff.  

I cannot figure how to copy from winff console.  Here is a little bit of it.

Stream #0.1: Audio: 0x0000, 44100 hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec for output stream #0.1

Any help would be appreciated as I am leaving for Japan tomorrow, and it Is a very long flight, a movie or two would be welcomed.

---

### Post by RageAgainstThis on 2008-09-04
I figured it out, not sure if I did it the long way or not, but it works.

I ended up compiling from the SVN and had to change the preset from mp3 to libmp3lame.  It is encoding now, so hopefully no more problems.

---

