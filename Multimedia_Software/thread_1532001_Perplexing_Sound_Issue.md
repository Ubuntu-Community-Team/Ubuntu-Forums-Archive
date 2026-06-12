---
title: "Perplexing Sound Issue"
date: 2010-07-15
forum: Multimedia Software
---

### Post by bvill on 2010-07-15
I am running 64 bit Lucid upgraded from Karmic.  I am finally getting everything tweaked and working the way I want it to except a sound issue that is driving me crazy.  On a fresh boot sounds come up and volume works as it should.  If I do a logout and login sound is muted and I have to go into sound preferences, check mute and then uncheck in order to get sound working again.

This is more of an annoyance than anything, but I want to get everything working correctly.  I have my sound preferences set to Ubuntu system sounds but even on a fresh boot I do not get the drum sound when the login screen comes up.  The default music does play while the desktop comes up but everything seems to get muted on a logout/login.  I have tried logging out and rebooting with sound preferences open checking and unchecking mute but nothing seems to work.

Does anyone have any suggestions.  What file should I be looking at to find a clue?  Any ideas would be greatly appreciated.

---

### Post by lidex on 2010-07-17
Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

No help? Comment out line 372 in /etc/init.d/alsa-utils
Should look like this when you're done:
```
# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```

---

### Post by bvill on 2010-07-19
lidex,

Thanks for the help. Worked by commenting out the line in your first suggestion. Still learning terminal commands and what files to look for and tweak. Finally getting my system set up how I like with help from folks like you in the community.  Thanks again.

---

### Post by lidex on 2010-07-19
You're welcome!

---

