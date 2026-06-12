---
title: "REGRESSION: FGLRX with 4850 and Ubuntu 9.10 Karmic"
date: 2009-11-05
forum: Multimedia Software
---

### Post by grigio on 2009-11-05
Fglrx worked with Jaunty but after the upgrade to Karmic it doesn't work anymore!!
Hardware driver install fglrx but the effects don't work.. :popcorn:

And the most important thing is that it in NOT mentioned in the Release Notes!

---

### Post by defensorfedei on 2009-11-05
I can confirm this as well.  There seems to be a regression with kernel versions 2.6.28-15 through 2.6.28-31. My graphics card does not seem to cope with any kernel upgrades as of late.  I hope that sooner or later, the fglrx support will be patched into later kernel releases.  

PS. this is with an ATI Radeon 3650HD graphics card.

---

### Post by markbuntu on 2009-11-05
I have a HD3650 and have had no problems with kernel updates. I am runnung hardy and jaunty and karmic. 

Distribution upgrades should not be attempted without removing all proprietary drivers beforehand, which you should do before installing the new drivers which the upgrade offers anyway.

Failure to remove old fglrx drivers before installing new ones will cause kernel modules to not be built with future kernel updates/upgrades.

---

