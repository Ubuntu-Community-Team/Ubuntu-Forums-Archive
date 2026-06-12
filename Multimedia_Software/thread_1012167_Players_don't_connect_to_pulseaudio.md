---
title: "Players don't connect to pulseaudio"
date: 2008-12-15
forum: Multimedia Software
---

### Post by christooss on 2008-12-15
I try to use pulseaudio but Im having problems with gnome players (rhytmbox and banshee)

They don't connect to pulseaudio so if I start them before for example gnome-mplayer and/or firefox + flash movie (that use pulse without problems) they doesn't play any sound.

If I take in to account these applications open gmplayer and firefox are listed in client tab of paman.

I have changed gstreamer-properties so it uses pulse but no changes in rhytmbox and banshee.

Any ideas?

btw: I have created /etc/asound.conf with pulseaudio configuration

P.S. I have tried totem which doesn't connect to pulse either so it must be something worng with gstreamer( I have installed gstreamer0.10-pulseaudio)

---

### Post by markbuntu on 2008-12-15
You need to get pulseaudio set up correctly

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

