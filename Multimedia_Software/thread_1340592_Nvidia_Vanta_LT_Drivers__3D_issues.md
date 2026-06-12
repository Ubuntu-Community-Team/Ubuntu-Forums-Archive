---
title: "Nvidia Vanta LT Drivers / 3D issues"
date: 2009-11-28
forum: Multimedia Software
---

### Post by Kraust on 2009-11-28
This has been talked about in a lot of topics and has never been resolved. I'm one of the few who still use this 10-year old 8MB graphics card and recently I wanted to try out playing an old game I used to play.

The issue is that, the Nvidia Drivers for this (Known as the nvidia-glx-legacy and more recently nvidia-glx-71 are non existent in Karmic.

They can be obtained from Nvidia's site but I've installed them prior (just removed them) and they're problem is that they don't work with Xorg. For some reason, whenever I write an xorg.conf file Xubuntu refuses to boot into gdm, requiring me to remove the xorg file and run with the default xorg file (which for some reason doesn't allow 3D rendering / glx)

Also, before anyone says it. There are not any "Restricted Drivers" There haven't been any since 9.04 (iirc). I'm on Karmic right now, and the only thing that is related to my Graphics Driver is the packages xserver-xorg-video-nv and xserver-xorg-video-nouveau which don't do anything and have no 3D support.

There's supposed to be a Driver that has 3D support (the official one from Nvidia's site) but Once again, I've never gotten that to work.

I've been working on this problem for around 10 hours today, I can probably solve all your answers.

---

### Post by Majki-Fajki on 2009-12-22
[http://ubuntuforums.org/showpost.php?p=8541137&postcount=8](http://ubuntuforums.org/showpost.php?p=8541137&postcount=8)

I,ve posted some info about that problem.

---

### Post by thedukesd on 2009-12-22
xubuntu 8.04 updated & GeForce 2 MX400

I followed this: [http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787)

All the attempts failled. Every time the same thing: low resolution and it's asking me to chose the drivers (all the proprietary drivers fail at test). I have to go back to the previsous settings...

---

