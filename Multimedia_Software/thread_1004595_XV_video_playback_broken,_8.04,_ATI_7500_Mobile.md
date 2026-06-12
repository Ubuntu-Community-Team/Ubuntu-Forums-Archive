---
title: "XV video playback broken, 8.04, ATI 7500 Mobile"
date: 2008-12-07
forum: Multimedia Software
---

### Post by rrwood on 2008-12-07
At some point, xv video playback seems to have broken for me.

I'm running Hardy, 8.04, on a Compaq N610C with the following video hardware: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500].


Playback of videos with Totem "Movie Player" or mplayer results in a green rectangle or box only.  Sound is fine, but not the video image.  Forcing the video output to not use xv (use x11 or opengl instead) results in things working perfectly, so it's not a video codec issue.


Anyone have any suggestions?

---

### Post by rrwood on 2008-12-07
Turns out that if I kick up from 16 bit to 24 bit display, then xv starts working again.

So, call this one solved, I guess.  There is still a bug in there somewhere though, since 16 bit used to work and now does not.


Dunno if 24 vs 16 bit depth is really any slower or not.  Feel free to comment, guys.

---

