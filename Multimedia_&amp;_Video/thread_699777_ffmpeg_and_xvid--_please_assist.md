---
title: "ffmpeg and xvid-- please assist"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by sekatsim on 2008-02-17
I've spent the last two days trying to get ffmpeg to convert xvid files, but to no avail. After rebuilding it entirely from source, and making sure xvidcore was included, I get:

> FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-xvid --enable-gpl
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Feb 17 2008 18:05:55, gcc: 4.2.3 (Ubuntu 4.2.3-1ubuntu2)
Unknown codec 'libxvid'


So.. xvid is obviously enabled-- why can't ffmpeg understand that?

Any help is appreciated.

---

### Post by stooshbunutu on 2008-02-19
Try using this ffmpeg front end, I find it makes things alto easier

It is called [winff]("http://biggmatt.com/files/winff-0.33-i386.deb") 

hope this helps you, it works great for me.:)

---

### Post by sgriso on 2008-02-20
yea, great but not helpful.. the problem is the same.. unknown codec libxvid :confused: (i have the same problem!)
EDIT: try [this]("http://ubuntuforums.org/showthread.php?t=593756"), it's helpful!! (read carefully the discussion)

---

### Post by philc on 2008-02-20
You need to --enable-libxvid not --enable-xvid as part of the ./configure command.

Here's how I did it:

[http://stream0.org/2008/01/install-ffmpeg-on-ubuntu-gutsy.html](http://stream0.org/2008/01/install-ffmpeg-on-ubuntu-gutsy.html)

---

