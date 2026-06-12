---
title: "VLC integrate video in interface"
date: 2009-04-26
forum: Multimedia Software
---

### Post by Venku7337 on 2009-04-26
Alright i just recently installed ubuntu 9.04, i then installed VLC when i play my videos i ran into a problem VLC will not allow me to intergrate the video into the interface now it just floats. I want to get to be integrated back in. I have tried changing the settings to make it so that was the case but even after saving the changes and restarting VLC it did not effect it. Any help would be nice, thanks.

---

### Post by Synt4x_3rr0r on 2009-04-27
There's a bug with the GUI in VLC >=0.9.2 that crashes VLC if the video is integrated on some computers. So the VLC devs decided to force it to not be integrated until it's fixed. Apparently it is fixed in the 1.x versions, but they're not able to backport it to the 0.9.x versions because it's a pretty extensive rewrite of the code or something. So we'll just have to live with it.

There is a patch to fix it on the 0.9.x versions though, but that would require compiling it yourself. Google "VLC integrate video in interface" and you'll find more info about it.

---

### Post by Namtabmai on 2009-04-27
There are a few PPAs about containing VLC with the required patch, so you need not compile it by hand.

---

