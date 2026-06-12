---
title: "Tried to fix sound; broke a lot of stuff..."
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by Bazarov on 2007-05-14
I was one of the lucky Toshiba laptop owners whose sound dies after upgrading to Feisty. I tried to fix it via the simple suggestion (a slight modification to modprobe.d/alsa-base), but =3stack, and =auto did nothing.

Ok, so I compiled and installed the latest Alsa drivers/utils/lib. Ran the snddevices script to populate the needed directories. Not only did this not fix it, I now have some extra issues:

-Kaffeine, Amarok, and Adept simply will not load.
-Konqueror will load, but will not close. I can close the window, but KSysGuard shows it still running. Requires a 'Kill' for each instance.
-NO sound modules are loaded. 

When I try to manually load sound modules, they look at the /lib/modules/2.6.20-15-**386**/kernel/sound/acore subdirectories (which are curiously empty) and fail. Most of the files they are hunting CAN be found in /lib/modules/2.6.20-15-**generic**/kernel/sound/acore subdirectories.

Have since tried apt-uninstall alsa + install alsa + install ubuntu-minimal, to no avail. Still no sound nor modules loaded...

Anyone have any keen insights? Have I done enough damage that I may need to reinstall Kubuntu (Edgy, thanks!)

---

