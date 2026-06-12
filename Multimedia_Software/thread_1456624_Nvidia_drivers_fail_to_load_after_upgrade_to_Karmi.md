---
title: "Nvidia drivers fail to load after upgrade to Karmic."
date: 2010-04-17
forum: Multimedia Software
---

### Post by Krovas on 2010-04-17
Laptop with Nvidia integrated GO 6100. Now stuck in low graphics mode.

Uninstall/reinstall ENVY. No joy.

"Hardware Drivers" reports that Nvidia drivers version 173 are activated at the moment, but not in use. Got the same report from the 185s. 'nvidia-xconfig' produced no results.

Not sure where to go from here. Please assist.

[SIZE=1]On a positive note, my onboard Broadcom wireless is working without ndiswrapper =)[/SIZE].

---

### Post by RedRat on 2010-04-17
Ok, I just got through trying to activate a proprietary driver through the hardware manager, and screwed my resolution up and basically was in very low resolution. Luckily I had EnvyNG in my System Tools menu. I was able to run that and restore my EnvyNG drivers and screen resolution. 

Try running
sudo envyng -g
in terminal.

I have only been able to get Nvidia installed via EnvyNG and no other way.

---

### Post by Krovas on 2010-04-18
Sokay, I got things up and running...after I upgraded to Lucid B2, and installed the x64 divers directly from Nvidia.

---

