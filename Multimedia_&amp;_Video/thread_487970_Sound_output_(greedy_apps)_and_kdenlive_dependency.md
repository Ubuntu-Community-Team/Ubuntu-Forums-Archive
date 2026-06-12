---
title: "Sound output (greedy apps) and kdenlive dependency"
date: 2007-06-29
forum: Multimedia &amp; Video
---

### Post by Arlanthir on 2007-06-29
I had my share of these situations and I'd really love someone to explain it to me / teach me a workaround..

eg.: I'm playing ePSXe (psx emulator) and I put the music effects at 0 and SFX at audible value. Next, I want to listen to my own music collection (instead of the game in question) and so I pump up rythmbox which REFUSES TO PLAY! Why does this 'no-share' of sound happens with most apps? Audacity, firefox, Rythmbox, ePSXe, all want all the sound for themselves!!

Next, when installing Kdenlive from 'Trevinos' Repository, I get a 'dependency not satisfiable: mlt' and I can't get this mlt anywhere (yeah, looks like I can't satisfy alright!).

Any insightful information? :S
Thank you very much!

---

### Post by Ubuntiac on 2007-07-14
You just need to install 2 other packages available on the same page of Treviño&#8217;s repository (at [http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/index.html](http://3v1n0.tuxfamily.org/dists/feisty/3v1n0/index.html)).

Just download the .deb files for mlt and mlt++ and install them (right click->Kubuntu package menu->Install package for those of us in Kubuntu). After that Kdenlive should install fine.

By the way, if you actually want to capture DV as well (fancy that) you need two other packages available from the repositories dvgrab and ffplay (in the package ffmpg).

Enjoy!

---

