---
title: "MPlayer"
date: 2006-06-25
forum: Multimedia &amp; Video
---

### Post by ChemPete on 2006-06-25
When I try to open any file i get this audio error:

[IMG]http://img61.imageshack.us/img61/2669/mplayer9tv.jpg[/IMG]

I installed "MPlayer 1.0pre8" with an automatic script posted [Here]("http://www.ubuntu-es.org/node/16574") (Spanish).

I also tried downloading the w32codecs, same problem.

---

### Post by detectiveinspekta on 2006-06-26
Looks like you are having problems with your sound card, from the look of things you don't get any sound at all?

I think you need to install alsa and/or oss through the package manager, when I installed all the sound was setup automaticly.
Good luck

---

### Post by ChemPete on 2006-06-26
Hi!, I have audio, in fact i`m hearing music with Rhythmbox right now. I presume this is a codec problem. Is there any way to reinstall the sound drivers for MPlayer?

PD: I already have alsa-base installed on my Ubuntu Dapper with Gnome.

---

### Post by eliabramo on 2006-07-08
I had the same problem, but when I switch to "sdl" it fixed.
the defult driver in my computer is alsa, but in mplayer it works with "sdl" and not with alsa or one of the other devices.

---

