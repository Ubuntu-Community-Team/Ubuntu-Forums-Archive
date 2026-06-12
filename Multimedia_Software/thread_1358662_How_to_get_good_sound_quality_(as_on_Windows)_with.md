---
title: "How to get good sound quality (as on Windows) without Wine?"
date: 2009-12-18
forum: Multimedia Software
---

### Post by Repgahroll on 2009-12-18
Hello there!

I just bought a mid-end 2.1 Edifier system, and I have a dual-boot machine, on Windows (XP 32) the sound quality is simply amazeing! I can hear a difference between WMP and Winamp/Itunes, the WMP quality is worst, however, when I boot on Linux (Ubuntu latest) i can hear an incredible difference, Totem (gstreamer) quality for mp3 is very poor, also rythmbox and mplayer are very very bad, and even the FLAC files has worst quality.

It isn't because of the volume level or equalizer settings, maybe the alsa/pulseaudio settings are weird, or even the players are bad. I also think it could be the module for my sound card that isn't any good, i have an onboard HDA (ALC888), i know it isn't the best sound card, but on Windows i get pretty good sound, and soon i'm going to buy an external one, but i don't want ti wait this to get decent sound on Linux.

I can run Winamp under Wine and i get a better sound quality (not as good as on Windows) but i would like to have a "native" solution for this... I don't believe there's no Linux user that has onboard sound and a 2.1 system.

Thank you very much.

---

### Post by jerrrys on 2009-12-18
maybe a quick fix would be VLC.  normally i would say to get it from package manager, but by downloading from the site you will get extra A/V packages.

[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)

---

### Post by saltmore on 2009-12-18
Worst case scenario remove pulse audio. There are guides how to do so.

---

### Post by Repgahroll on 2009-12-19
Thanks guys.
Pulseaudio sounds better than ALSA/OSS.

I've installed SongBird and the sound is a little better, don't know why because i think songbird uses gstreamer.

What is the best audio player for sound quality? Amarok, Banshee, Exaile?

Thanks.

---

### Post by Repgahroll on 2009-12-19
SOLVED!!

I've installed AUDACIOUS and ticked the option:
"Bypass all of signal processing if possible"

Thnaks everyone.

---

### Post by jerrrys on 2009-12-19
> **Repgahroll said:**
> SOLVED!!

I've installed AUDACIOUS and ticked the option:
"Bypass all of signal processing if possible"

Thnaks everyone.

thats a good trick to know

---

