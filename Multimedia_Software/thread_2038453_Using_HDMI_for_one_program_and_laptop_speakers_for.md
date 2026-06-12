---
title: "Using HDMI for one program and laptop speakers for another"
date: 2012-08-06
forum: Multimedia Software
---

### Post by db579 on 2012-08-06
Is it possible to have one program (Banshee for example) set to always play any audio over HDMI (if connected) while the rest of the system outputs any audio over the laptop speakers or headphone jack etc...?

---

### Post by Woegjiub on 2012-08-28
Sorry for bumping this if it is too late, but I just had the problem of wanting XBMC to output through my TV, and everything else through my speakers.

Turns out, all you need to do is install 'pavucontrol'
It is a GUI app which gives you more control over pulseaudio, including the ability to do what you want :D
All you'd have to do is have the app running, chose the audio output for that app in PulseAudio Volume Control, and you're done :D

---

### Post by micahpage on 2012-08-28
I thought you had to have 2 audio cards?

---

### Post by Woegjiub on 2012-08-29
> **micahpage said:**
> I thought you had to have 2 audio cards?
Nope, pulseaudio seems to allow the one card to direct programs to separate speakers.
I know that in KDE, this stuff is in the default settings, and it was actually a major cause of annoyance when I didn't realise that at one point.

---

