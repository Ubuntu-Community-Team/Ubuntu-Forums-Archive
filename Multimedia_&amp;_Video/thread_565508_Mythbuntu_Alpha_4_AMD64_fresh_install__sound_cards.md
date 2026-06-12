---
title: "Mythbuntu Alpha 4 AMD64 fresh install / sound cards detected, but no audio"
date: 2007-10-02
forum: Multimedia &amp; Video
---

### Post by obscure411 on 2007-10-02
OK, so here's the issue...

I've got a fresh install of Mythbuntu 7.10 Alpha 4.  It has two sound cards, an onboard Realtek ALC 660 and an AOpen AW-870LP occupying a PCI slot.  I've done an apt-get dist-upgrade on it, and everything is up-to-date.  MythTV is working properly, and I've imported a previous mythdb and recordings.

Life is good... EXCEPT... no audio.   lspci shows both cards, and the XFCE mixer control shows both as well.  ALSA mixer shows no channels muted, audio is cranked, but ... nothing.  Zero.  Zilch.  Nada.

Although I'm pretty good at troubleshooting my own issues, I've never really had to configure a soundcard under Linux before, and I'm not sure what I should be searching for.  Any pointers on where to start?

---

### Post by tgm4883 on 2007-10-02
mythtv is probably using a different audio card.

Try pluggin it into the other card and seeing if you get sound.  If you do, it's an easy fix to get it to use the other card.

---

### Post by obscure411 on 2007-10-02
Tried that already.  No sound from either card, in myth or in XFCE attempting to play MP3's, movies, etc.

---

### Post by obscure411 on 2007-10-02
<BUMP>

Isn't there some sort of a "sudo dpkg-reconfigure alsa" that I can do to just redetect and configure alsa?  The cards are detected by an lspci -l and an aplay -l...

Help??

---

### Post by am_pcguy on 2007-11-04
Did you ever get this sorted out? 

I have the exact same problem.  I have sound set up in MythTV for video's and TV but MP3's do not have sound.

---

