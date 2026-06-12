---
title: "[SOLVED] mplayer memory leak"
date: 2008-07-04
forum: Multimedia Software
---

### Post by noway on 2008-07-04
I'm using mplayer-nogui version: 2:1.0~rc2-0ubuntu13+medibuntu1 on Ubuntu 8.04 64bit, and my graphic card is the internal Intel G33. 

The last two movies I've watched (.mkv x264 720p) started lagging after a while and then I had to end the process from System Monitor. I watched the process in system monitor and just after a few seconds memory starts building up fast. I've seen it go as high up as 1.2gb before I have to end the process and restart the movie. 

I haven't had this problem before but I haven't made any changes either so I have no idea what the problem might be.



---edit---

There is a memory leak in libass [http://bugs.gentoo.org/213638](http://bugs.gentoo.org/213638)

The solution is to disable *** subtitles which can be done by adding this to your config:

***=off


---edit---

Ubuntuforums decided to censor my edit. *** should be ssa backwards.

---

