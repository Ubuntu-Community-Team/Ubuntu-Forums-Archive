---
title: "New kernel and Nvidia :("
date: 2005-12-22
forum: Multimedia &amp; Video
---

### Post by awakatanka on 2005-12-22
After installing a new K7 kernel and uninstall all other old kernels  i tryed to install nvidia again. But ofcourse it doesn't work X doesn't want to start and say it can't find nvidia driver. I followed the how to's and every topic that i found on the forums but it just don't want to start.

nv is working but as soon as i have changed it to nvidia it falls back to command line. And i tryed everything. on 386 kernel it worked but stupid as i am i didn't hold a save copy of that working kernel :). 

Please if anyone has idea's for me post it because my head hurts and i'm close to break something :D .

---

### Post by az on 2005-12-22
linux-restricted-modules-2.6.12-9-k7 - Non-free Linux 2.6.12 modules on AMD K7
linux-restricted-modules-2.6.12-9-k7-nvidia-legacy - Non-free Linux 2.6.12 modules on AMD K7


Is one of them installed too?

---

### Post by awakatanka on 2005-12-23
[QUOTE=azz]linux-restricted-modules-2.6.12-9-k7 - Non-free Linux 2.6.12 modules on AMD K7
linux-restricted-modules-2.6.12-9-k7-nvidia-legacy - Non-free Linux 2.6.12 modules on AMD K7


Is one of them installed too?[/QUOTE]
You my hero, somehow i i didn't installed those 2 files.

---

### Post by az on 2005-12-23
Use one or the other - the legacy if for older nvidia cards and the regular is for more modern cards.

See the long description of the packages.

---

