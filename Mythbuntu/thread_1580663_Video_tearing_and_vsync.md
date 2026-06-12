---
title: "Video tearing and vsync"
date: 2010-09-23
forum: Mythbuntu
---

### Post by drbisio on 2010-09-23
Is there a way to synchronize video rendering with v-sync in myth?

I'll appreciate any help !

thanks, bye

---

### Post by ian dobson on 2010-09-24
Hi,

I think there's an option in the frontend under setup,playback to use v-sync.

Regards
Ian Dobson

---

### Post by LowSky on 2010-09-24
i can confirm there is an option for v-sync under the frontend under setup > playback

---

### Post by drbisio on 2010-09-24
Tryed to enable opengl as renderer and now I can't  navigate mythtv menus !!!!!

I can reach only the first and second menu layer, not the menu where there is the renderer option !!

How do I roll back the configuration ?

Is there a way to reset all settings ?

I tryed removing and reinstalling mythtv package but it didn't worked !!

Help !!

---

### Post by yonkiman on 2010-10-08
> **drbisio said:**
> Is there a way to synchronize video rendering with v-sync in myth?

I had to add ```
Option "Composite" "Disabled"
``` to xorg.conf to get rid of my tearing a few years ago.  Don't know if it's still necessary (they may have improved the driver), but it worked at the time.  More info here:

[http://ubuntuforums.org/showthread.php?t=872130](http://ubuntuforums.org/showthread.php?t=872130)

Good luck!

---

