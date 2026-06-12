---
title: "Low fps and no sound in quake1-based games after installing ubuntustudio-audio..."
date: 2010-02-01
forum: Multimedia Software
---

### Post by SymenTimmermans on 2010-02-01
Situation before:
Running nquake(ezquake) with sound and around 40fps (onboard video)

I don't know why, but I installed the ubuntustudio-audio metapackage (and dependencies).
After discovering how totally useless that was, I uninstalled all the packages ubuntustudio-audio installs.

Now I get the following error on the console when I run nquake/ezquake:
[PHP]
/dev/dsp: Input/output error
[/PHP]
My framerate has dropped to 7 or 8 fps. Even when I run with the command line -nosound, the framerate still doesn't increase.

I tried the solutions from the comprehensive audio problems guide, and all is as it should be. I removed and reinstalled alsa, I removed and reinstalled pulseaudio, and I removed all jack-related packages.

This problem is related to all Quake-engines. UrbanTerror and Enemy Territory are not affected. The FPS drop is the same when using Wine.

I installed the latest xorg packages from UbuntuX, to no avail. 


I know this could be an application/configuration problem instead of a distro problem, but I really think this is related to something ubuntustudio-audio did, and I'm just hoping someone might have experienced similar issues toying around with ubuntustudio stuff on a regular (x)ubuntu installation.

---

