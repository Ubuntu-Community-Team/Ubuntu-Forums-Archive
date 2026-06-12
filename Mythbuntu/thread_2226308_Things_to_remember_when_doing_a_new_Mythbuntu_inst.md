---
title: "Things to remember when doing a new Mythbuntu install"
date: 2014-05-26
forum: Mythbuntu
---

### Post by DeweyOxberger on 2014-05-26
Yet another note to my future self:

1) You start installing Mythbuntu and during the install the graphics go crazy.  You are faced with pixel insanity.  Reboot, restart the install, and this time hit a key, bring up the menu, and go into options and set nomodeset


2) Then, remember to run the first system update from apt-get, NOT from the Software Updater.  Software updater can't or doesn't prompt you for the samba "did you want to keep the config file" or some such thing.  It will appear to hang the update.  Just run update manually dude.

14.04 up and configured in less than 45 min (sans default audio which took an additional 1.5 hrs to figure out).  Not bad in 2014.

---

