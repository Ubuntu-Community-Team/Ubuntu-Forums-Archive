---
title: "New iPod - can't play music"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by BuzzardBoy on 2008-04-06
So, I had an old iPod classic that just recently died, so yesterday I went and bought a new 80 gig 6th generation iPod.  I had no problems with my old iPod using gtkpod, but now I'm having problems.  I tried to load my music onto the iPod, but when I eject it, the iPod says there is no music on it.  The music files are there on the iPod when I explore it on my desktop, but the player just doesn't recognize them as music.

I've tried to use other programs (Amarok, Banshee, Rythmbox, etc), but all with the same results - the files are on the iPod, but it won't play them and registers "No Music".

Any ideas?

---

### Post by soga_genzo on 2008-04-06
Support for the 6th generation iPods has only been introduced with libgpod 0.6.0 (which is the library underlying gtkpod and any players supporting the iPod). Gutsy uses 0.5.2, while 0.6.0 is included in the upcoming Ubuntu 8.04 release.

---

