---
title: "Converting videos to play in Windows"
date: 2007-02-22
forum: Multimedia &amp; Video
---

### Post by Dphin on 2007-02-22
I'm trying to share some videos from my digital camera with friends, and I'm trying to find a codec that will work with a standard installation of Windows XP. The files the camera produces are huge, so I've been using FFMPEG to convert them, but I haven't found any codecs that work. I though that MPEG2 would work with anything, but when I tried to run it on my housemate's computer, there was no error but the video was completely scrambled.
What codecs can I use, and is there some other option that I need to make things work on Windows?

---

### Post by reader4 on 2007-12-13
Not sure if you ever found your answer, but I generally use MPEG1 when I know portability is an issue (in PPT presentations). I keep a simple script (that I can run using Nautilus Actions with a right-click) for these videos:

ffmpeg -i $1 -vcodec mpeg1video -b 500k $1_ppt.mpg

---

