---
title: "H264 slower on linux?"
date: 2006-08-03
forum: Multimedia &amp; Video
---

### Post by katzman on 2006-08-03
First of basic system specs:
pentium m 1.86ghz processor
1g ram
nvidia geforce 6600go 128Meg video card
Ubuntu Dapper Drake running Gnome

My problem is that in windows i can play h264 videos just fine using 35~40 percent cpu. But in linux it takes all the cpu and stll cn't keep up. This happens in xine mplayer and totem (gstreamer 10). Every other video codecs plays fine.

Is this happeening just because the linux libs for h264 are not as mature yet or do i need a slight setup change?

oh and vlc just gives corrupted graphics

---

### Post by katzman on 2006-08-13
no one?

---

### Post by katzman on 2006-08-15
so i solved my own problem....setting the video codec family to DirectSHow codecs in Mplayer lets me play h264 videos even on a 900mhz athlon i use as media box

---

