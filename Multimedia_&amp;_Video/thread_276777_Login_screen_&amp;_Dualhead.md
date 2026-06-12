---
title: "Login screen &amp; Dualhead"
date: 2006-10-13
forum: Multimedia &amp; Video
---

### Post by grayFalcon on 2006-10-13
Hello everybody!

I'm having a bit of an issue here. I decided to use my old CRT as a second screen - no good wasting a perfectly good VGA-out on my graphics card.

Now, I've gotten it set up so far. I can log in, I get both screens working separately (without TwinView - don't want that).

The problem is, no matter what I do, I always get the login screen on my CRT. How do I tell xorg which of my screens to use as the "main" screen? I haven't been able to find anything about that on the internet, and my experiments (with the CRT's resolution at 800x600 and the TFT's at 1280x1024, to be able to keep them apart) have only led me to the conclusion that there must be some vodoo with a bit of black magic going on there. Just please tell me that there's an easier way than sacrificing a virgin at full moon :(

Thanks a lot in advance,
-Wojtek

---

### Post by CatKiller on 2006-10-14
It's a black lamb sacrifice for xorg.conf configurations. Virgins are for wireless networking.

I think that the login screen gets displayed on whichever screen is your "Screen 0", defined first in the ServerLayout section.

---

