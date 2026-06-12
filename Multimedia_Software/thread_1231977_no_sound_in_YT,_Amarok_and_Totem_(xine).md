---
title: "no sound in YT, Amarok and Totem (xine)"
date: 2009-08-05
forum: Multimedia Software
---

### Post by bloody_hell on 2009-08-05
Hey,

I got no-sound problem in some applications like for example Amarok and during playing movies on Youtube.

I can hear the sound in Rhythmbox, Totem etc. I read somewhere that you just have to install: phonon-backend-xine but it didn't fix anything..

I noticed recently that in Totem (GStreamer version) everything works fine while in Totem (xine) I get no sound at all, so propably there's something wrong with this xine (whatever it is).

To be honest I've been using Ubuntu for few days only and I'm quite a big noob so please, if you know the solution, try to post some detailed-noob-explanation :P (like: now click on the yellow icon with left mouse button :P )

If it helps I got standard soundcard integrated with motherboard P5N-D - Realtek ALC883

Thanks in advance!
TP

---

### Post by bloody_hell on 2009-08-07
Problem status for 7/8/2009:

Amarok - no sound. Dunno how it happened but it was ok for a while, but then it stopped working again. Now when starting Amarok a message appears:
[IMG]http://zapodaj.net/images/27a7df5e46f2.png[/IMG]
..and then no sound of course.

Youtube - sound is working 
Rhythmbox - sound is working

Any ideas how to fix this?

---

### Post by alexandari on 2009-08-07
Are you using ALSA? Make sure you are. Open the **sound preferences** and select alsa. Tweak it,see what works for you. If you havent installed alsa
**sudo apt-get install alsa** in the terminal
Rhythmbox and Totem are using OSS by default. May I suggest better programs for opening videos and music?
I would suggest using **VLC** or Mplayer for the videos :) and
Audacious or **Exaile** for music

Good luck!

---

### Post by bloody_hell on 2009-08-07
> **alexandari said:**
> Are you using ALSA? Make sure you are. 
I am :)
> **alexandari said:**
> May I suggest better programs for opening videos and music?
I would suggest using **VLC** or Mplayer for the videos :) and
Audacious or **Exaile** for music
I know Totem sucks - it was just an example, I liked Amarok thou. I'll try Audacious and **Exaile**, but anyway it would be nice to find out why Amarok doesn't work and how to fix it :P

The other thing bout Amarok is that I can add songs to playlist but they're not beeing added to music collection (so it's not possible to sort it). It was like this from the beginning, even in the short period of time when Amarok worked

---

### Post by markbuntu on 2009-08-09
Amarok and totem use xine which is for KDE and KDE4 uses phonon for its sound server but you cannot control phonon soince you are not running KDE. You need to work around that by changing the xine default directly which there is no option to do in Amarok or Totem or VLC anymore so you need the xine user interface (ui). You can get the xine ui and use that to set the xine settings to pulseaudio or alsa. That's what I ended up doing.

I think the xine ui is called ui-xine in the repository.

---

### Post by bloody_hell on 2009-08-10
Problem solved using xine-ui. Thanks

Second part of the problem was that I used for some time Alien DAC and I it seems that it's not supported by xine programs (or maybe only I don't know how to configure it - nvm)

BTW, IMO Exaile > Amarok - that also solves my problem :D

---

