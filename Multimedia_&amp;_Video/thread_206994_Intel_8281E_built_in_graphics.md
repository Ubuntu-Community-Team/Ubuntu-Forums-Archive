---
title: "Intel 8281E built in graphics"
date: 2006-07-01
forum: Multimedia &amp; Video
---

### Post by djheadley on 2006-07-01
OK, guys and gals, I messed up.  I got a newer machine (bare bones HP 7855) and did a direct drive transplant from my old machine (433Mhz Celeron).  What can I say, I wasn't paying attention.  Anyway, Now I can't get X to start.  I've tried this:
sudo dpkg-reconfigure xserver-xorg
followed by:
sudo /etc/init.d/gdm start

and no deal (no X).

The HP 7855 has the following:
MB - Trigem Computer Inc., Cognac
video - Intel 8281E (built in)
sound - AC'97 driver for Intel 82801AA
monitor - IBM 2235 C50

Any suggestions short of re-install?
:confused:

---

