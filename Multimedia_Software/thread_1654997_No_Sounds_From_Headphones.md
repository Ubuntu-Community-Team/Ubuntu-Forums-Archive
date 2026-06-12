---
title: "No Sounds From Headphones"
date: 2010-12-29
forum: Multimedia Software
---

### Post by kiki298 on 2010-12-29
My speakers are working, but my headphones aren't. Music keeps playing from the speakers when the headphones are plugged in. I've looked around, and found out some stuff about ALSA, but I haven't been able to fix my problem, so I put my output info below. I have an Asus, it's model number is U52F-BBL9. I'm running Ubuntu 10.10

This is my output:

[http://www.alsa-project.org/db/?f=c95cc568ef74bdb60e26b8e98c7b89dabea5e995](http://www.alsa-project.org/db/?f=c95cc568ef74bdb60e26b8e98c7b89dabea5e995)

Thanks for any help! :)

---

### Post by Rhubarb on 2010-12-29
You may have some luck playing around with alsamixer.
Open up a terminal, and run **alsamixer**
There you can mute / unmute / change volume / etc all sorts of sound stuff.

I'm not familiar with that motherboard, so I can't help you too much in that department. - But messing around with alsamixer I find fixes many problems such as this.

---

### Post by kiki298 on 2010-12-29
Okay, I found a solution!

First, I opened this file for editing in terminal.

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

then, I entered this line into the end of the document. 

```
options snd-hda-intel model=auto
```

Save and reboot!

Totally worked for me, hopefully it will work for anyone else who finds this, although I suspect it varies depending on your computer model what you enter into the document.

---

