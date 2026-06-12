---
title: "Amarok and iPod classic 80Gb"
date: 2008-08-26
forum: Multimedia Software
---

### Post by LoermansA on 2008-08-26
Hi all,

I might be doing something dumb (wouldn't be the first time) but I can't get Amarok to recognize my iPod Classic. Other programs do see it and can copy music to/from it or play music off of it (Songbird, gtkpod for example), but not Amarok. I've tried to manually add my iPod to Amarok's DAP's, but it refuses to see it as an iPod. All this is on Ubuntu 8.04 64 bit.

Any help?

Regards,

Arjan

---

### Post by LoermansA on 2008-08-28
Nobody? How can Amarok not see my iPod while all the other programs can? It means it's not a libgpod problem.

---

### Post by LoermansA on 2008-09-12
Hi all,

I'v found out what the problem was, my iPod was registered as LOERMANSA'S. It's mountpoint was /media/LOERMANSA\'S/. The ' character apparently causes problems for Amarok. After changing the iPod's mountpoint it started working.

Regards,

Arjan

---

### Post by smellydog on 2008-09-22
Hi there.  Sorry i was not gleaning the posts, but i would have helped you out, at least tried.  Glad to see that you got it working.  But as for the mount point problem, i would not have guessed that!  Good to know now!

---

