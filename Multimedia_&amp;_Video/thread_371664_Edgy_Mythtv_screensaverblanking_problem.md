---
title: "Edgy Mythtv screensaver/blanking problem"
date: 2007-02-27
forum: Multimedia &amp; Video
---

### Post by Confusatron on 2007-02-27
After nursing a partially broken Kubuntu 5.10 mythtv box for far too long, I finally found time to update it to Ubuntu 6.10 (Edgy) based on this excellent guide:

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)

I had a couple of sound issues that I worked through (and am still having issues with my cheapo saa7134 card), but for the most part, everything works for watching videos. I didn't even have to compile a custom sis video driver!

The one major problem I have is that the screen keeps going black during video playback! It is definitely a screensaver or power save thing, since moving the mouse gets rid of it... 

The guide I used installs gnome-screensaver and runs it in the /usr/local/bin/mythtv.sh script, which seems counterproductive - or is the idea that gnome-screensaver will kick in after some idle time on the static mythtv menu (to prevent burn in) but that it should be mplayer aware?

---

### Post by superm1 on 2007-02-27
> **Confusatron said:**
> After nursing a partially broken Kubuntu 5.10 mythtv box for far too long, I finally found time to update it to Ubuntu 6.10 (Edgy) based on this excellent guide:

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend)

I had a couple of sound issues that I worked through (and am still having issues with my cheapo saa7134 card), but for the most part, everything works for watching videos. I didn't even have to compile a custom sis video driver!

The one major problem I have is that the screen keeps going black during video playback! It is definitely a screensaver or power save thing, since moving the mouse gets rid of it... 

The guide I used installs gnome-screensaver and runs it in the /usr/local/bin/mythtv.sh script, which seems counterproductive - or is the idea that gnome-screensaver will kick in after some idle time on the static mythtv menu (to prevent burn in) but that it should be mplayer aware?
The idea is that the screensaver does kick in on static screens.  All media players (including mythtv) are patched to have gnome-screensaver support.  Considering you had 5.10, do you still have xscreensaver installed too?  When are you getting it blanking - during myth usage?  Or during media player usage, or when?

---

### Post by Confusatron on 2007-02-28
I wiped the old kubuntu install, so xscreensaver is not there. The screen is going blank during video playback in mythtv, for which I am using mplayer. 

Update: it is definitely gnome-screensaver, I changed it to "feet" with /usr/bin/gnome-screensaver-preferences and they start dancing madly after 10 min of viewing... I guess I will leave it out of the scripts for the short term.

---

