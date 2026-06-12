---
title: "Clicking mouse has no effect upon boot"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by CSMatt on 2007-11-30
I just finished trying several different ways to get Dual screen working with my ATI card.  I installed the proprietary drivers, realized that they didn't work at all for dual screen (and Compiz didn't work either) and uninstalled them.  I tried using Xinerama as per the instructions in [this](https://help.ubuntu.com/community/XineramaHowTo) wiki entry but apparently Gutsy doesn't like Xinerama.  I tried the radeon driver but that didn't work either.  Eventually I reverted my xorg.conf to what it was when I started.  Now occasionally upon boot it seems that X just ignores mouse clicks.  Mouse movement is just fine.  Restarting X with Control-Alternate-Backspace seems to fix it, but it's really annoying.  Is there some way that I can find out what's going wrong with the X server to cause it to occasionally ignore mouse clicks?

---

### Post by CSMatt on 2007-12-02
Bump.

---

