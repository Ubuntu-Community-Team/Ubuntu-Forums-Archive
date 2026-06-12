---
title: "libGL.so"
date: 2006-09-23
forum: Multimedia &amp; Video
---

### Post by CatKiller on 2006-09-23
I'm running two graphics card at the moment - one Geforce 2 GTS and one Ati Rage. I've got the nvidia drivers installed, so I get 3D stuff on one monitor (UT seems to work better than in Windows hooray!) but not the other. Fair enough, I thought, the atimisc driver doesn't do 3D, no problem.

I booted off the Live cd to do some messing about with the filesystem last night, and it only initialised the Ati card - which is fair enough - but it did pretty reasonable 3D things. I had a look in the xorg.conf from the Live environment, and it doesn't seem to do anything particularly funky. So I might be able to get 3D on both screens.

I understand that the nvidia driver comes with its own libGL.so, and some other files, and makes symlinks from these files to the generic library names. Is it possible to configure the drivers so that this doesn't happen? To clarify - so that the driver on the left screen uses the appropriate libraries for the Nvidia card, and the driver on the right screen uses the appropriate libraries for the Ati card. Using symlinks makes perfect sense if you only want to use one thing, but not if you'd like to use more than one.

---

### Post by CatKiller on 2006-09-23
So does no one here knows about graphics drivers in Linux? I only really want to know if it's possible.

---

### Post by tseliot on 2006-09-23
> **CatKiller said:**
> To clarify - so that the driver on the left screen uses the appropriate libraries for the Nvidia card, and the driver on the right screen uses the appropriate libraries for the Ati card. Using symlinks makes perfect sense if you only want to use one thing, but not if you'd like to use more than one.
AFAIK you should use 2 cards of the same kind (manufacturer) in order to do that.

I hope to be wrong though (since I've never tried it myself).

You can try asking here:
[http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by CatKiller on 2006-09-24
If they were both by the same manufacturer, they'd both be using the same driver in the first place, and I wouldn't need to tell them to do something different.

Thanks for the link. I'll prowl around there when I'm back at my own computer.

---

