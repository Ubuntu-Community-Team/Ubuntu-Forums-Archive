---
title: "nvidia driver updated on gutsy!"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by lordViN on 2007-10-21
I've just installed a fresh install of gutsy, but I have noticed that the nvidia-glx-new is now updated to the latest version 100.14.19.

in order to install the driver, 

> sudo aptitude install nvidia-glx-new

is enough to make it work?? or I need to do anything else?

---

### Post by FredB on 2007-10-21
Just use restricted manager. It will install automatically the driver, set up your xorg.conf and after a reboot, you'll have the driver working without problems.

---

