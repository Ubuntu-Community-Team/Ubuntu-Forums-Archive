---
title: "Problem under Gutsy - Miro and web browser"
date: 2007-11-03
forum: Multimedia &amp; Video
---

### Post by agamotto on 2007-11-03
I have been having problems playing video since I have installed Miro under Gutsy.  The program starts, downloads fine.  Whenever I try to play a video with a Firefox or Thunderbird window on the screen at the same time, the video corrupts turning into what looks like a scrambled television station.  Alternatively, as soon as I open either program after having started Miro, the whole system just freezes.  This only happens when I have a web browser or email program running.  

Any ideas as to what is going on?

Randy

---

### Post by agamotto on 2007-11-20
I have been experimenting around, and discovered that neither Gutsy or Automatix installed the w32 codecs, or if they did, not in the right place.  I fetched them from the Mplayer home, put them in /usr/lib/win32 dir with sudo, and videos are working, with the occasional glitch.  

Not fixed, but better.  I still can't figure out what the connection is between the codecs/video and Firefox that is locking up my system...

---

