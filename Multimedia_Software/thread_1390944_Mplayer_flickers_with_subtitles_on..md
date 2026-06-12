---
title: "Mplayer flickers with subtitles on."
date: 2010-01-26
forum: Multimedia Software
---

### Post by Muminboll on 2010-01-26
Im running ubuntu 9.10. Got the latest ATI drivers.

I've been having problems with tearing. Or maybe its not really tearing, its more of a vsync problem with horizontal lines coming up when there is too much action going on in a movie.

Anyways, I finally managed to find a sulotion, running mplayer with the X11 (OpenGL) video output. That makes it run without tearing in fullscreen, but not in windowed mode, which i find pretty strange. But since I always watch movies in fullscreen it dosnt really matter.

The problem now is that subtitles makes some movies flicker on the TV via HDMI! Not on my laptop monitor. Im running 60hz on both so that shouldnt have anything to do with it. Big black vertical lines flicker around on the bottom 1/3 of the screen. 

Anyone has a solution for this?

Also: is there any other player that can run the X11 (OpenGL) output? Ive tried all options in VLC, all gives me tearing.

---

### Post by Muminboll on 2010-01-26
Bumb! 

Really no one has had problems with flickering subtitles? It was really hard finding anything of value when searching for the problem, so this thread is needed :)

---

### Post by phrog on 2010-02-09
Try mplayer with -vo xv

Also it could be a video ram issue. It was for me.
[http://blog.phrog.org/2010/02/08/black-flickering-lines-in-mplayer/](http://blog.phrog.org/2010/02/08/black-flickering-lines-in-mplayer/)

---

