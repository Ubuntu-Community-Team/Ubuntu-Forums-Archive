---
title: "what is jack (for) ?"
date: 2009-04-06
forum: Multimedia Software
---

### Post by henky on 2009-04-06
Hey guys, I tried searching around a little but couldn't find what I am asking myself,
I have ubuntu studio to record my vocals and integrate them with songs, I absolutely love it, but how can I benefit from jack? what is it and how do I use it?

thanks!

---

### Post by neu2buntu on 2009-04-06
jack is more or less a mixer for your soundcard,... it lets all your audio programs "talk" directly with each other.... you will most likely want the frontend (gui) qjackctl. it takes a fair bit of setting up tho, i use ubuntu-studio inside ubuntu -intrepid and use jack for all my audio apps

---

### Post by neu2buntu on 2009-04-06
heres a usefull post that covers most sound scenarios ,and theres a section about ubuntu-studio and jack [http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack](http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack)

---

### Post by henky on 2009-04-06
> **neu2buntu said:**
> jack is more or less a mixer for your soundcard,... it lets all your audio programs "talk" directly with each other.... you will most likely want the frontend (gui) qjackctl. it takes a fair bit of setting up tho, i use ubuntu-studio inside ubuntu -intrepid and use jack for all my audio apps

Hi, ok thnx for the quick reply! but still I do not quite understand, what is the benefit of those audio programs talking, can I somehow incorporate  it into my use of ubuntu?

---

### Post by neu2buntu on 2009-04-06
you will most definately need jack for audio work of any type, and nearly all audio apps have an option to run through jack....   one example that i use is is i record vids i have made in lmms and the only way i could get qtk-recordmydesktop to record the live audio running through my soundcard was to run lmms and recordmydesktop through jack(qjackctl)....   what are you using for your projects eg audacity,ardour etc?


[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

---

