---
title: "Can't change resolution with 845G"
date: 2007-05-12
forum: Multimedia &amp; Video
---

### Post by fo0b4er on 2007-05-12
I just installed Ubuntu, and I can't change the screen resolution at all.  No matter what I do it stays stuck at 640x480.  I know my monitor can support higher resolutions because I also have Windows XP on the computer, and it can run properly at 1024x768.  If it helps the exact specs of my graphics controller as shown by lspci are: "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)".  I have tried a few guides that use 915resolution, and I have tried manually editing xorg.conf, but nothing has allowed me to change the screen resolution.  Any help would be appreciated! :)

EDIT:  I also tried the intel driver (xserver-xorg-video-intel), which looked good in gdm but crashed the xserver after I logged in.

---

### Post by fo0b4er on 2007-05-13
Found a solution, posted here: [http://ubuntuforums.org/showthread.php?p=2647985#post2647985](http://ubuntuforums.org/showthread.php?p=2647985#post2647985).  Solution found here: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsIntel) :) :) :)

---

