---
title: "ALSA, OSS, PulseAudio, Jack, ...?"
date: 2008-12-15
forum: Multimedia Software
---

### Post by osterchrisi on 2008-12-15
Hello,

I'm circling around these topics for nearly a months now but it seems as I'm still as clever as before.

I use a M-Audio Delta Audiophile 24/96 + a Microsoft LifeCam VX-1000. With the card I want to play sounds and record music through the inputs (works with ALSA, OSS, Jack), with the webcam I just want to talk through Skype (recording works with none - seems like Skype playing sound works with OSS only).

I'm trying different combinations of all these sound servers and sound systems now for weeks, but I can't find a working one.
I use Ubuntu 8.10 and I freshly installed it approximately one month ago, so I'm quite new to all this Linux-stuff but I'm learning swift.

Could anyone plz give any hint about these different sound servers/systems? Is there a "golden combination" or a "better" and a "worse" server/system? And which combination of all of these can I use to get the three simple tasks done:

- play sound through M2496
- record sound through M2496
- record voice for Skype through VX-1000

Thanks for any suggestions, I really appreciate it as I spent days and weeks in various forums already.

PS: Right now I use OSS, have PulseAudio deinstalled.

---

### Post by zettberlin on 2008-12-19
> **osterchrisi said:**
> Hello,

I
PS: Right now I use OSS, have PulseAudio deinstalled.

There is no OSS in a modern Linux unless you are on ppc - its all ALSA, that has a OSS-compatiblity layer.

With your card I suspect you want to do more then just listening to video soundtracks and system sounds ;-)

So if you are into music-making I recommend you use jackd for everything, though this is not well supported in Ubuntu. If you use KDE+Phonon you can build xinelib from source to make your desktop jack-aware. You need to destroy everything related to xinelib that comes from the Ubuntu-repos to make this work but it does work very well.

Install the development-packages for GTK, QT4, KDE4, jackd, alsa, libsoundfile and some more related stuff - the dev-packages are still just great in Ubuntu - you can install what you need by compiling it then, if you do not found a good solution in the repos (such as in the case of xinelib...)

---

### Post by markbuntu on 2008-12-19
You can go here for some info about how things work and how to get your sound dialed in. Be sure to follow the links to anything that interests you


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

