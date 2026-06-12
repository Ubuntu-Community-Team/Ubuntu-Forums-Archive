---
title: "Removed pulsaudio to install esound -&gt; gnome-volume-control won start"
date: 2010-01-11
forum: Multimedia Software
---

### Post by owoaux on 2010-01-11
I was having problems with ubuntu's overall speed so i decided to look for optimization threads here and i've found [this](http://ubuntuforums.org/showthread.php?t=1152095). From there i've followed the link to [How to Remove Pulse Audio Ubuntu 8.10 (Intrepid Ibex)](http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html) and decided to give it a try even though it's for 8.10... which obviously was a mistake. I guess you could say i've successfully uninstalled pulseaudio in order to install esound, now everything works faster but i can't seem to open gnome-volume-control (waiting for the sound system to respond)
> 
$ gnome-volume-control

** (gnome-volume-control:6114): WARNING **: Connection failed, reconnecting...

** (gnome-volume-control:6114): WARNING **: Connection failed, reconnecting...

So i guess i should change some line in some file that thinks i'm still using pulseaudio. Would you tell me how to do that?

---

### Post by Yellow Pasque on 2010-01-11
If you're using Karmic/9.10, use this PPA: [https://launchpad.net/~dtl131/+archive/ppa](https://launchpad.net/~dtl131/+archive/ppa) (Lucid versions coming soon)
You want the gnome packages from it. Don't install the (lib)canberra stuff or the portaudio packages, as they're intended for OSS4 users.

---

