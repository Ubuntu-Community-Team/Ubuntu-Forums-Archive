---
title: "Kodi will not load in an upgraded Ubuntu 18.04.1 box"
date: 2018-08-18
forum: Multimedia Software
---

### Post by havok1977 on 2018-08-18
Hi

So I decided to upgrade from 16.04 LTS to 18.04 today for a Kodi dedicated box and Im already regretting it.

- Upgrade went fine, installed all the packages and the nvidia driver.
- Upgraded to latest release from Kodi PPA
- Lightdm settings are unchanged and as required

Kodi will no longer auto load, when I invoke it from the CLI i get:

$ kodi
ERROR: Unable to create GUI. Exiting

All X dependencies are met, X is up and running yet all I get on my screen is a blinking cursor.

root     11845  0.0  0.5 102616  8776 tty7     Rs+  21:54   0:00 /usr/lib/xorg/Xorg -bs -nolisten tcp :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch


I found this searching on Google, but it hasn't helped so far - the grub stuff mentioned does not make sense to me

[https://www.smarthomebeginner.com/ubuntu-boot-to-kodi-2-ways-to-boot-directly-to-kodi-on-ubuntu-systems/](https://www.smarthomebeginner.com/ubuntu-boot-to-kodi-2-ways-to-boot-directly-to-kodi-on-ubuntu-systems/)

Where can I look for logs that will give me useful hints? Any help will be appreciated

---

### Post by TheFu on 2018-08-19
It won't help now, but I always wait to upgrade on my kodi machines to avoid most of these issues.

That article is from before 18.04 release.  Many things changed in 18.04, so instructions could easily be incorrect for 18.04.

My 16.04 Kodi system doesn't have _-seat seat0_ or _-bs_ in the xorg options. Those options are not in the manpages for 16.04  xorg, so they must be new?

All logs are in /var/logs/ somewhere.

---

### Post by havok1977 on 2018-08-19
I figured it out, I needed the nvidia-340 driver for my old-ish GPU instead of the newer version.

X was falling back to Nouveau and didn't load as expected.

Got rid of the newer Nvidia and Nouveau drivers. All good now, thanks

---

