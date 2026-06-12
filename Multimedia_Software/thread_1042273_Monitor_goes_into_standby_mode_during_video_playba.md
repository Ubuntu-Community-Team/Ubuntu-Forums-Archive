---
title: "Monitor goes into standby mode during video playback"
date: 2009-01-17
forum: Multimedia Software
---

### Post by rem on 2009-01-17
Hello friends,

Since upgrading to Intrepid, even I have set the power management tool in "Preferences" never to blank the screen and even I have set in Mplayer and other video players (Totem, SMPlayer, Xine) to stop the screensaver during video playback, my monitor keeps going to sleep after a while ... Is this a known bug, is there anything I could do to stop this annoying behavior?

Thanks a lot!

---

### Post by utnubuuser on 2009-01-17
Hello -- Some machines have sleep functions built into the BIOS; -- Might be adjustable.

---

### Post by rem on 2009-01-17
> **utnubuuser said:**
> Hello -- Some machines have sleep functions built into the BIOS; -- Might be adjustable.

This is happening only since upgraded to Intrepid had no troubles on the same PC under Breezy up to Hardy ... just to be sure I will check the BIOS.

Thank you.

---

### Post by mc4man on 2009-01-17
There's some xorg entries someone posted that work very well, have to run so can't search out.

What you could also do is leave your power management setting at 'never' and then go to screensaver settings. Leave the screensaver unchecked but set the 'regard the computer as idle' to a time below when it's going to sleep. 5-10 min will do.

Power management doesn't kick in till the computer is considered idle even when set to never.
This way after 5-10 min the never will kick in before the bios mode has a chance to take effect.

---

### Post by rem on 2009-01-17
ok, will try that and get back with the results. thank you and sorry, have to go watch a movie now :)

---

### Post by rem on 2009-01-17
> **mc4man said:**
> There's some xorg entries someone posted that work very well, have to run so can't search out.

What you could also do is leave your power management setting at 'never' and then go to screensaver settings. Leave the screensaver unchecked but set the 'regard the computer as idle' to a time below when it's going to sleep. 5-10 min will do.

Power management doesn't kick in till the computer is considered idle even when set to never.
This way after 5-10 min the never will kick in before the bios mode has a chance to take effect.

yep, working thanks a lot mc4man, owe you one... if you somehow will manage to find the xorg stuff i will be greatful. cheers!

---

### Post by rem on 2009-01-17
P.S. How do you mark a post as solved? Thanks!

---

### Post by mc4man on 2009-01-17
Here's the link, never used because I'd already set up the idle time/power management ect. 

[http://ubuntuforums.org/showthread.php?p=6482839#post6482839](http://ubuntuforums.org/showthread.php?p=6482839#post6482839)

post 7

The solved has been disabled for the moment.

---

### Post by rem on 2009-01-17
> **mc4man said:**
> Here's the link, never used because I'd already set up the idle time/power management ect. 

[http://ubuntuforums.org/showthread.php?p=6482839#post6482839](http://ubuntuforums.org/showthread.php?p=6482839#post6482839)

post 7

The solved has been disabled for the moment.

Thanks!!

---

