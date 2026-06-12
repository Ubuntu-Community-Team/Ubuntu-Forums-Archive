---
title: "gnome-mplayer"
date: 2011-05-13
forum: Multimedia Software
---

### Post by beew on 2011-05-13
Gnome-mplayer suddenly stopped working in both 11.04 and 10.10 today.

In 11.04, when I opened any video file it just shows a white screen and the status bar below simply said "stopped". It works again when I change Audio Output from "Default" to HDA ATI SB (STAC92xx Analogue) (alsa). But then some hd videos become choppy unlike before (playback was smooth before). What was "default" and why does the old setting which has been working suddenly cease to work?

In 10.10 (one of my 10.10 install, the other one works fine), gnome-mplayer has stopped working a few weeks ago, setting video output to be blank solved the problem.[http://ubuntuforums.org/showthread.php?t=1741277](http://ubuntuforums.org/showthread.php?t=1741277) 

But today it has stopped again. Opened any video or audio file just showed a blank screen and the status bar said "stopped". But it works again when I change the video output from blank to xv or vdpau.

In other words I have to do exactly the opposite to what I did before to get it working again. 

Why does this happen? It seems rather strange. Also VDPAU is not actually working, it shows the video but cpu usage is ~70% whereas with Smplayer it is ~ 15% for the same video (so it is not a mplayer problem)

Thanks in advance to anyone who can offer some insights into what causes such strange behaviour.

---

