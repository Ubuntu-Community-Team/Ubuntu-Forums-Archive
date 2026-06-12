---
title: "wrong vid driver"
date: 2007-11-17
forum: Multimedia &amp; Video
---

### Post by tgpqaz on 2007-11-17
i have a compaq presario 1600 and just installed 7.10 my screen is too small so i played around with driver  s for the display  i installed a compaq driver and when i restarted the screen was messed up. i can login but can't do any thing else. is there some way to fix it with out reinstalling.

---

### Post by Qwerty_ on 2007-11-18
Try reconfiguring your xserver. When you are at the login screen hit ctl+alt+f1. 

You should now be presented with a terminal.

Run

```
sudo apt-get reconfigure xserver-xorg
```

---

### Post by rondamato on 2007-11-18
Hello,

As a newbie I must ask this: is xvidtune still used to "correct" small screen problems like having the image a bit too wide or tall?  I remember using it all the time in BSD to fine-tune my xorg.conf modelines because my admin was anal and he didn't let me "fix" the image using the CRTs built-on controls (now THAT'S a UNIX geek!) but this was long ago in a distant galaxy when Win95 (and CRTs) ruled the Earth...  Now that I think about it LCDs have probably made those timings (flyback, dotclock, H/V sync, etc) obsolete.

No need to answer, just wondering for wondering's sake...

Thanks!

DoctorRon
Chicago, IL
<rondamato@gmail.com>
------------
v7.10 Gutsy Gibbon 32-bit/Gnome
HP Pavillion (something)
AMD Sempron 3100 w/2GB DDR 533

---

