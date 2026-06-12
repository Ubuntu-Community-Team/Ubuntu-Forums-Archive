---
title: "nvidia driver crushes system"
date: 2011-07-24
forum: Multimedia Software
---

### Post by Cnaeus on 2011-07-24
I installed lubuntu 11.04 recently to replace my old xubuntu system. Lubuntu has proven to be faster to boot up & uses less memory than xubuntu, so I would really like to stick with it, but I cannot get nvidia drivers to work... When I installed the latest nvidia driver  & saved the xorg.conf file, the graphics went totally messed up at the next reboot. I mean, even the logo screen was an unreadable mess of black and white lines, and then it showed some error message, or whatever, I can only guess what it was, becouse it consistet some 2 or 3 lines of totally unreadable text. Then it failed to bring me any further, so I had to boot up from live cd, ad use an xorg.conf backup to make the system functioning again. This way the logo is still the mess of lines I mentioned, but the lxde desktop interface works. Hovewer, without the driver I cannot set a lower resolution (defauld screen settings manager doesn't work for some reason, it never did, in fact) and the browsers are awfully lagged, too.
I would appreciate any help, thank you.
System specs:
Intel Celeron 2Ghz
512 MbRam
256 Mb Nvidia GeForce 6600
Abit BD7III Moterboard

---

### Post by Cnaeus on 2011-08-01
Seems like I had to uninstall the nouveau driver first, as I didn't realize that it was installed as default. I guess it caused some problems when both drivers were present.

---

