---
title: "ffmpeg outputs VERY bad video"
date: 2010-08-07
forum: Multimedia Software
---

### Post by jose158 on 2010-08-07
I tried to encode a video into avi and mp4 from a test video I made using GTK-recordMyDesktop, but the output is HORRIBLE:

[http://www.youtube.com/watch?v=zSYITsWhvBo]("http://www.youtube.com/watch?v=zSYITsWhvBo")

---

### Post by bildr on 2010-08-07
use mencoder instead...ffmpeg craps out on me all the time when the input file is ogg.

not sure why, but that's how i handle it...

something about the file structure being iffy when it is produced by gtk-record.  conversions from cheese webcambooth went fine with ffmpeg too.

i am convinced it is a file format issue with gtk-record.

another option is to use kdenlive to import the video and play with it. then you can render it to whatever.  this works more often than not, but sometimes i get kdenlive crashes when working with ogv

---

### Post by ron999 on 2010-08-07
Yes, use mencoder instead.
There's a how-to here:-[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566&highlight=upload+youtube]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1501566&highlight=upload+youtube")

---

### Post by FakeOutdoorsman on 2010-08-07
You can still use FFmpeg, but you'll need to compile it to work with those oddball videos from recordMyDesktop (although Ubuntu Maverick Meerkat's FFmpeg is probably recent enough).  I've described each step here and it's easier than it looks:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by jose158 on 2010-08-07
Thank you! It works!

---

