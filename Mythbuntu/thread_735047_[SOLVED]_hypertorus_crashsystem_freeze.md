---
title: "[SOLVED] hypertorus crash/system freeze"
date: 2008-03-25
forum: Mythbuntu
---

### Post by a_posse_ad_esse on 2008-03-25
Hey all, I upgraded to Hardy, and my system freezes within a few minutes of startup.  I finally found a crash report for hypertorus, and I think that the problem may be related to the screensaver in general.

I would prefer to not have a screensaver at all, as the system is connected to a TV and remote, but I can't find how to disable it.  I have (from before)  the appropriate settings in the control center as well as in xorg.conf, but still get the "random" assortment of screensavers.  Is there a new way to disable it?

If not, how do I fix hypertorus?

---

### Post by a_posse_ad_esse on 2008-03-25
The system freezes seem to have been caused by the screensaver problem.  There seems to have been a setting that was overwritten that I had overlooked; I had to go into settings-> screensaver and disable it there too.

---

