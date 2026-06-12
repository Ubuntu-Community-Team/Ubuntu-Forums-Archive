---
title: "&quot;Watch TV&quot; stopped working"
date: 2008-12-22
forum: Mythbuntu
---

### Post by korgman on 2008-12-22
The picture just froze yesterday while watching OTA HDTV.  I reboot Mythbuntu and selected 'watch tv'.  The screen goes blank for a second, then returns to the main menu.  At this point I tried a DVD which worked except no sound.  alsamixer had muted the digital output.  I un-muted that and got sound.

I did a channel scan from setup, and Mythbuntun found all my OTA local DTV stations.  Still nothing when I select "Watch TV".  I'm using the Hauppauge 1250 tuner card.

Any logs I can look at?  Something I could run/look at from the command line?

---

### Post by iponeverything on 2008-12-22
You probably just need to repair the database.

[http://ubuntuforums.org/showthread.php?t=691766&highlight=mysqlcheck](http://ubuntuforums.org/showthread.php?t=691766&highlight=mysqlcheck)

---

### Post by korgman on 2008-12-22
That worked.  Thanks!

---

