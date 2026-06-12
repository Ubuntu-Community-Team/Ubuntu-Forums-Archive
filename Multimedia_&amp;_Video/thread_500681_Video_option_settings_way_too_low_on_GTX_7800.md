---
title: "Video option settings way too low on GTX 7800"
date: 2007-07-14
forum: Multimedia &amp; Video
---

### Post by dlouwers on 2007-07-14
Hi,

I am using an NVidia GTX7800 card. When I want to tune my display through system->pref.->screen resolution I am getting horribly low options:

1024x768 @ 54Hz max.

On other operating systems this card on this monitor is capable of outputting 1200x1024 @ 75Hz. Why can I not choose that setting on this system and how can I fix this?

---

### Post by pppZero on 2007-07-15
Sounds like you might be using the default nvidia driver.

Go to System -> Administration -> Restricted Drivers Manager and enable "NVIDIA Accelerated Graphics Driver"

After downloading/installing/configuring everything for you, Ubuntu will tell you that yo have to reboot. When you log in again, run (from a terminal, or Alt-F2) nvidia-settings. This should let you use whichever resolution you desire :)

I Just looked and System -> Preferences -> Screen Resolution should give you new resolutions after enabling the driver too.

---

