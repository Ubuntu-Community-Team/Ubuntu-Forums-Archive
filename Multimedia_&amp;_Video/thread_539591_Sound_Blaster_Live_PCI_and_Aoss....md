---
title: "Sound Blaster Live PCI and Aoss..."
date: 2007-08-31
forum: Multimedia &amp; Video
---

### Post by kstinson on 2007-08-31
When i installed flash i had no sound.  After looking around i reconfigured the firefox dsp to use aoss.  Restarted and the sound worked.  Then i restarted again later, not installing or changing anything and it didn't work.  So i checked the config file and it was still at aoss.  Anyway i rebooted again and the sound came back.  Shut the computer down for the night, came back to it the next day and the sound was not working again.  However this time i noticed that i don't get the gnome startup sounds either when flash is not working.  So after all the trouble of rebooting i decided to try a few things.  So far it seems that sudo asoundconf set-default-card Live gets the sound working again without rebooting.  So i am guessing this is a conflict between my sound blaster live card and the onboard sound, but why?  The bios is set to disable the onboard, and the mixer is set to use the Live card.  Is there a work around that i am missing here?  I really want to fix this, cause while opensuse was rock solid for me it very slow for having a 2ghz AMD 3000 processor.  Oh by the way, i used Kubuntu 7.04 alternate for a short time and the sound worked flawlessly from install with no changes.  I just prefer the gnome desktop and am using Ubuntu 7.04.

---

### Post by kstinson on 2007-09-03
Well i didn't get any responses but luckily i figured it out on my own.  For anyone that has this same issue i managed to fix it using.

gksudo asoundconf list

gksudo asoundconf set-default-card Live

I also left my firefox config files left to FIREFOX_DSP "aoss"

It seems it was merely the os switching back and forth between the two cards until i manually set it to only use the Soundblaster Live card.

---

