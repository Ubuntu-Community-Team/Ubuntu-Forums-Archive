---
title: "Unable to remove Jovie (Voice Synthesiser)"
date: 2015-10-08
forum: Multimedia Software
---

### Post by Sam_Grace on 2015-10-08
The error might possibly be that my computer has the trusty tahr 14.04 installation and the software is for KDE.

But I have tried the commands:

sudo apt-get remove jovie

sudo apt-get remove --auto-remove jovie

sudo apt-get purge jovie

sudo apt-get purge --auto-remove jovie

and the commands have been successful and it states that the software has been removed however, whenever I turn on the sound back on, all I heard it Jovie.

Is it that there is a whole world of start-up software folders that I haven't accessed? if so where and how to I remove them?

---

### Post by ajgreeny on 2015-10-08
Have you rebooted to make sure that the utility has been closed and can not restart when you startup again?

Removing the package will not always stop something working if it is already running; rebooting should manage to stop it.

---

### Post by Sam_Grace on 2015-10-08
After a reboot I noticed that there is a screen reader function in accessibility options that could be turned off with "ALT + SUPER + S".
Thank you for your time.

---

