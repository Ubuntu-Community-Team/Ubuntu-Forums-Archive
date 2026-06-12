---
title: "ATI Driver &amp; Gnome-System-Monitor"
date: 2006-07-23
forum: Multimedia &amp; Video
---

### Post by ephman on 2006-07-23
hi,

i have an ati m300 128mb card in an inspiron 6000 notebook.  i just installed the latest ati driver off ati's site, all's cool, installed pretty easily.  but something i've noticed is that now all of a sudden the gnome-system-monitor shoots up over 50% of my cpu.  so i uninstalled the driver and kaboom back down again.  has anybody seen this issue yet, or is my system-monitor insane?

thanks,
ephman

---

### Post by Dubbayoo on 2006-07-23
mine is normal, less than 3%.

---

### Post by ephman on 2006-07-23
hi,

when i use the mesa driver i'm around 3% as well for the gnome-system-monitor.  just the ati driver i think is doing something to the system-monitor.  i can't imagine what, but it's funny when i uninstall the ati driver things are cool.  strange.

ephman

---

### Post by ephman on 2006-07-23
hi,

ok came across this link [Click Here]("https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/30570").  basically i had to go back to the 386 kernel so that i could use the ati driver and not have the gnome-system-monitor go bonkers.  so there must be something up witht that.  wish i chould use the 686, but i can't find a fix for this issue.  things seems to be alright now, i'm not maxing out the cpu for basically no reason.

ephman

---

