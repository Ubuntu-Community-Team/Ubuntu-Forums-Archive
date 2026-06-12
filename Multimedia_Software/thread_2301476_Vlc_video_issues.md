---
title: "Vlc video issues"
date: 2015-11-02
forum: Multimedia Software
---

### Post by scopes2 on 2015-11-02
Hi

I am new to Ubuntu. I have installed Lubuntu 14.04 on an old PC (Celeron 2Ghz and 1M ram) to get acquainted with the OS. 
I have installed "lubuntu-restricted-extras".  

My problem is with VLC player and Mplayer not displaying video when playing a video file. Audio seems to be fine.

Attached pse find LXTerminal output when running VLC.

Your input will be appreciated

scopes2

---

### Post by SeijiSensei on 2015-11-02
That machine doesn't have enough horsepower to watch most modern videos, especially anything in 720p or better.  Modern, highly-compressed codecs like H.264 require a pretty hefty CPU to decode the video in real time.  If you can find an older video encoded in XviD in the AVI container, preferably one in 480p, see if that plays for you.  Most of those date back to 2008 or before.

You can try these: [http://thud.us/videos/misc/xvid-samples/](http://thud.us/videos/misc/xvid-samples/)

---

### Post by scopes2 on 2015-11-03
Hi SeijiSensei thank you for input. I am trying to watch 360p video which I used to watch while running VLC in Win XP on this machine.

---

### Post by scopes2 on 2015-11-03
Problem solved. played around with display output selections and unselected "accelerated video output" in VLC preferences.

---

