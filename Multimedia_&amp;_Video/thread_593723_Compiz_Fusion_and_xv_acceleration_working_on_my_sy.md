---
title: "Compiz Fusion and xv acceleration working on my system!"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by adx442 on 2007-10-27
I hope this helps someone out ... from my web searches, it looks like most people had given up on xv video playback with Compiz Fusion enabled.

I have an Nvidia 7900GT video card, with the latest nVidia drivers (installed via Envy), and Compiz Fusion enabled.  When I would play a video in Ubuntu for the first time, it would play perfectly, but when I would close the player (totem-xine or mplayer, it didn't matter which one), the next video would play with sound, but a green screen for the video output.  I used xshm as the video output, and that worked fine, but with dropped frames.

Simply changing /usr/bin/compiz to show:

INDIRECT="yes"

and restarting the x server and compiz (or a reboot) allowed xv to work perfectly on my system, with Compiz enabled and working beautifully.

I hope I'm not the odd case for this to work, and that nVidia has changed something in the newest drivers so that this works now.

---

### Post by roaldz on 2007-10-27
I´ve always been able to play video with totem, and I have an NVidia 7600 Go. Is this special?

---

