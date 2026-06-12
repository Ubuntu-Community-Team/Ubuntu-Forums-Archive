---
title: "No browser gives sound . . ."
date: 2010-04-08
forum: Multimedia Software
---

### Post by justin.rixx on 2010-04-08
I am using Kubuntu Lucid Beta 1. I have since yesterday. I don't get sound from anything in a web browser (Youtube, Pandora, etc.) though I can get mute video. I can get sound from Amarock, Dragonplayer, system sounds, etc. But yeah, nothing from a web browser (Konqueror, Google Chrome or Firefox)

Any help appreciated!

Thanks

---

### Post by pebe on 2010-04-25
I have something like the same problem, I think I had it on 9.10 also. Sometimes when I watch some videos on youtube etc the sound automatically mutes. also everytime the song changes in spotify the sound automatically mutes. its a real annoyance and totally takes a way the should be pleasant experience of enjoying music, when I after each song have to turn the volume up again eftar automatically being muted after each song. 

problem still there after new installation of ubuntu.

big problem should really be looked at and fixed asap.

---

### Post by pebe on 2010-05-04
fixed my problem, it seemed to be a problem with the dedault wine not working properly with the pulseaduio system. the solution I did was to change in wine configuration (under the Audio tab) unclick anything else and change to the EsounD driver as pulseaudio is able to emulate EsounD. Another fix that I havenät tested is to get a pulseaudio enabled version of wine.

heres a link with guide to a repository with pulseaudio enabled wine, made for ubuntu 9.10, maybe it works for 10.04 alsa..

hope others get helped by this, strange if ubuntu don't have pulseaudio enabled in their default wine as standard

---

