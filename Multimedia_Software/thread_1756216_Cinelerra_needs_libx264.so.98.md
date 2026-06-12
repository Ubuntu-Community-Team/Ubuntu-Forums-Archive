---
title: "Cinelerra needs libx264.so.98"
date: 2011-05-12
forum: Multimedia Software
---

### Post by Weepleman on 2011-05-12
Hi, I've been using cinelerra for a while now, and all of a sudden, it says that I need libx264.so.98.  When I looked for this in Synaptic, I saw the package, but when I clicked the checkbox a popup told me that it was not supported or something like that.  Now libx264.so.98 is gone when I search for it in synaptic.  The only thing I can think of that changed since the last time I used cinelerra was that I ran apt-get autoremove.  I really need cinelerra for a project I'm doing, so any help would be greatly appreciated.  Thank you

---

### Post by Weepleman on 2011-05-12
I have libx264.so.85, libx264.so.106, and libx-dev installed

---

### Post by no2498 on 2011-05-12
[http://www.g-raffa.eu/Cinelerra/HOWTO/index.html](http://www.g-raffa.eu/Cinelerra/HOWTO/index.html)

[http://heroinewarrior.com/cinelerra/cinelerra.html](http://heroinewarrior.com/cinelerra/cinelerra.html)

[http://www.lightworksbeta.com/](http://www.lightworksbeta.com/)

top two should help you
last one is some thing to look at you may like

---

### Post by Yellow Pasque on 2011-05-12
When Cinelerra was built, it was linked against libx264-98, which you had until you autoremoved it. The solution is to get a more recent Cinelerra, by building it yourself or using and updated PPA. I guess you could technically install the 98 package again too: [http://packages.ubuntu.com/maverick/libx264-98](http://packages.ubuntu.com/maverick/libx264-98)

---

### Post by Weepleman on 2011-05-12
Yay it worked!  I had already tried installing cinelerra from the cinelerra ppa, and that didn't work, so I tried reinstalling libx264-98.  That did the trick.  Thank you!

---

