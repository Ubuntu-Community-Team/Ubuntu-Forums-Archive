---
title: "[SOLVED] GXine playback choppy after libdvdread3 installed"
date: 2007-09-26
forum: Multimedia &amp; Video
---

### Post by pyrodrake on 2007-09-26
I've been trying to work this one through for a while, but I can't seem to find any posts or forums on this exact situation, so hopefully someone will be able to help me...

I have an older laptop (P3 1ghz) that I acquired, and its been working beautifully with Xubuntu.  I've been using it to watch AVI files with gxine, and it would play them, although slightly choppy, but the audio and video were almost always in sync, and I had nearly no problems with it.

This laptop has a DVD drive on it, and I wanted to be able to play encoded DVD's, so I followed the post [here.]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/dvdplayback.html")  Now, DVD's play beautifully in gxine (better than AVI's did, actually).  Now here is where my problem comes into play.  After I installed libdvdread3, whenever I try to play an AVI with gxine, the video and audio loose sync.  The audio continues to play, but the video is playing at a slower rate.  when it reaches a point where the audio is about a minute ahead of the video, the audio cuts out completely and the video continues to play (still at a slower rate and more choppy).

At this point, my main question is how do I fix this so I can play DVD's and still be able to play AVI's?  Or, if I can't fix this, how can I uninstall libdvdread3?  If you just know the answer to THIS question, please let me know!  I would rather have the ability to play AVI's than DVD's.  :)

I'm not sure if anyone would need any information as far as additional software/settings/hardware, so please just let me know and I'll post anything I have.  Thanks!

---

### Post by pyrodrake on 2007-09-26
I normally don't bump threads, but I'm a bit desperate here.  ;)
Also, just an update, I tried to apt-get remove libdvdread3, libdvdcss, and libdvdcss2 and have the same results.  :(

---

### Post by pyrodrake on 2007-09-28
Fixed the problem.  Ended up reinstalling Xubuntu from scratch.

---

