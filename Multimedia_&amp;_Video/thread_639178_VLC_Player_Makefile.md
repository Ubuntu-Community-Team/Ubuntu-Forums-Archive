---
title: "VLC Player Makefile?"
date: 2007-12-12
forum: Multimedia &amp; Video
---

### Post by XtremeBlaze on 2007-12-12
I have noticed that when installing tarballs you need "makefile.am", "makefile.in" and "makefile". When I downloaded the tabal for VLC Player it only had "makefile/am" and "makefile.in", no "makefile".

Can someone either upload the makefile for this application so i can drag it into the directory, or tell me how to create this makefile that I'm missing.

(I have build-essential installed, and when in the terminal I type "make" with the directory chosen, it comes up with the error " **No rule to make target 'install' " )

Any help is much appreciated :)

---

### Post by mc4man on 2007-12-13
Either you've oversimplified your post or you're not getting what your trying to do. Here's a howto for feisty, should be possible to adapt for gutsy.(read thru comments) 
While I've successfully compiled some simpler apps this is above my know how (what to enable ect.), so I think I'll give it  a try or two or three on my test box, good way to learn.
if your successful  would be nice to know how/what you did
[http://www.jbkempf.com/blog/post/2007/05/06/Build-VLC-media-player-under-Ubuntu-Feisty-704](http://www.jbkempf.com/blog/post/2007/05/06/Build-VLC-media-player-under-Ubuntu-Feisty-704)

---

### Post by mc4man on 2007-12-15
Actually a very interesting way to compile/install vlc, there were about 6 add. packages needed than listed and i had to eliminate the \'s in the ffmpeg code. Ended up with ver. 0.9.0-svn

---

