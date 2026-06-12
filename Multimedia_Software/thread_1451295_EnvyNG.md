---
title: "EnvyNG"
date: 2010-04-10
forum: Multimedia Software
---

### Post by PinchedNerve on 2010-04-10
I have it installed on 9.10 but when I try to use it, it doesn't open.  What do I need to know? I have an issue with a desk top that's using a Toshiba LCD TV with the ability to be used as a monitor. Its native resolution is 1360 or 1366 x 768 & the best Ubuntu with allow with the nVidia drivers is 1024x768. I can change the resolution, but can't save it & when I reboot its back to 1024x768. Tried Envy to update the drivers but its not doing anything after I click it. Envy is installed.

Old windows veteran but extreme n00b to Linux.

---

### Post by WinterRain on 2010-04-10
Do:
```
gksudo nvidia-settings
```
To change resolutions. You don't need envyng for anything.

Make your changes, then "apply", then "save changes to X configuration file. You may have to reboot after that.

---

### Post by PinchedNerve on 2010-04-10
Saving the changes is the problem, it won't let me.

As far as the code, I've no idea where I would add that. I've found the xorg.conf file but I can't see where I would manually change the resolution. Like I said, n00b here on Linux.

Edit: Ok, so I found "terminal" & added your code, luckily I was then able to save the settings.

Thanks!

---

