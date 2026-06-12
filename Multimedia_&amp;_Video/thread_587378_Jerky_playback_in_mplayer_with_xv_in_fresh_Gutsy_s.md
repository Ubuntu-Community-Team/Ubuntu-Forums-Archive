---
title: "Jerky playback in mplayer with xv in fresh Gutsy system"
date: 2007-10-22
forum: Multimedia &amp; Video
---

### Post by Nameless_one on 2007-10-22
I am experiencing the infamous jerky playback in mplayer with xv, although for none of the usual causes (from what I can tell) :( 

Playback is jerky both in fullscreen and normal-size, and only with xv. I also tried vlc with xv, and it happens there too. 

I installed Gutsy today, everything is fresh. I am using the fglrx driver, I think I performed all the checks: xv is supported and xv overlay is enabled, OpenGL overlay is disabled, my card is supported etc.,etc. 

x11 works, although I am trying to avoid it, as it uses a software zoom which uses CPU and is sometimes also jerky. I had problems with it in the past, and now that I have proper Xv support, I want to make the best of it. 

Any ideas? :(

EDIT: It seems I always find the solutions to my problems right after I post them somewhere. I found [here](http://ati.cchtml.com/show_bug.cgi?id=677) that using mplayer's -nodouble, solves this - and it worked for me. It is a fglrx bug. I will post any updates, more troubles or whether the newest fglrx solves this, if I install it.

---

### Post by DFreeze on 2007-10-23
Keep us updated. It seems there's a lot of people experiencing trouble with fglrx and video (including me).

---

