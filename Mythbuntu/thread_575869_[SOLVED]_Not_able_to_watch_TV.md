---
title: "[SOLVED] Not able to watch TV"
date: 2007-10-14
forum: Mythbuntu
---

### Post by w00tfest99 on 2007-10-14
I'm trying out my first mythtv system (and first linux system) with mythbuntu.  I've installed everything but when I go to "Watch TV" all I get is a black screen.  If I go into the logs in the "Information Center" there are no error messages.  I've pulled in the listings guide fine from schedules direct.  I have the Hauppauge PVR-150 (with remote).  I'm able to watch DVDs, listen to audio, but no tv.  Any help in diagnosing my problem would be appreciated.

---

### Post by w00tfest99 on 2007-10-14
I've now managed to get just 2 channels to "work" (they're both fuzzy and the color goes in/out) by switching the tuner type from V4L to MPEG-2.  Is my new problem just a signal problem?

---

### Post by superm1 on 2007-10-14
Sounds like the wrong frequency table selected in mythtv-setup to me.

Make sure you are using the appropriate options, us-cable for cable in the US, etc.

---

### Post by w00tfest99 on 2007-10-14
Yeah, I have it set to us-cable.  Any other suggestions?

---

### Post by w00tfest99 on 2007-10-14
ah-ha! I needed to set it to us-cable-hrc.  Thanks for the help

---

