---
title: "Dual Screen w/o Xinerama"
date: 2009-10-23
forum: Multimedia Software
---

### Post by Kastang on 2009-10-23
Hey all, 

I have a Radeon 4870 card. I have two monitors, running at 1680x1050, and 1280x1024 resolutions. I had my monitors configured using ATI drivers from ATI website along with Xinerama. This allowed windows to be dragged across monitors.

The issue is, I would like to run certain features that require Compiz/Composite to be enabled. Which is not possible when Xinerama is enabled. I reset my xorg file and uninstalled the ATI drivers. This reverted the system back to the default drivers. I am able to set up a virtual screen via the Display tool that comes with Ubuntu, everything works fine (Proper resolutions, can drag items, can run Docky, etc etc.. ), the only issue is that every time I logout, or restart the settings are reverted to default (2 mirrored screens and low resolutions).

- How can I have the settings not revert every time I log out or restart my computer?

- Is this possible to do with ATI drivers while not using Xinerama but keeping Composite features enabled?

- Is there another driver option that may suit me better then the default (non ati) driver I am currently using now to achieve dual monitors. 

Thank you.

---

### Post by markbuntu on 2009-10-23
First of all, do not use the System/Preferences/Display tool with the proprietary driver. Use the Catalyst Control Center. You can set a big desktop in the Catalyst Control Center if you turn xinerama off. Be sure to restart after each change you make or bad things can happen.

Is that a 4870x2???

The latest 9.10 driver is out now and a lot of the desktop configuration stuff that was problematic before is fixed. You should get that. Be sure to remove the old driver before installing the new one or you will have problems with kernel updates.

---

