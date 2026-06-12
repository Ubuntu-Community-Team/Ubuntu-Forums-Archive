---
title: "Matrox G400 dualhead on Hardy 8.04"
date: 2008-05-03
forum: Multimedia Software
---

### Post by mark1softie on 2008-05-03
Has anyone got Xinerama working on Hardy Heron, on a Matrox G400/G450/G500 graphics adaptor?

Had dual-head working fine on Gutsy Gibbon, using mga_drv.so & mga_hal_drv.so [first with official [www.matrox.com](www.matrox.com) MGA driver v4.4.0 drivers, then with unofficial tuxx-home.at MGA driver v4.4.3].

Upgrade to Hardy Heron [internet download, using the "Update Manager" tool stopped the second screen working.

The updated /etc/X11/xorg.conf looks OK, with both screens defined, Xinerama enabled, etc., but /var/log/Xorg.0.log shows:
"(II) LoadModule: "mgahal"
(WW) Warning, couldn't open module mgahal
(II) UnloadModule: "mgahal"
(EE) Failed to load module "mgahal" (module does not exist, 0)"
...
"(--) MGA(1): Chipset: "mgag400" (G400)
(EE) MGA(1): This card requires the "mga_hal" module for dual-head operation
        It can be found at the Matrox web site <http://www.matrox.com>
(II) UnloadModule: "mga""

Copied the previously-working mga_drv.so & mga_hal_drv.so to /usr/lib/xorg/modules/drivers/ and adding 'Load "mga_hal"' to the Module section.

Next restart of the X server failed: It finally restarted in failsafe mode.

Tried trawling the Matrox website for newer drivers, without success.

Currently working on one screen, with the default version of mga_drv.so.

From the Xorg error messages, I suspect there should be an mgahal_drv.so driver, but it isn't included in the Hardy Heron xserver-xorg-video-mga package.

Anyone got around this problem, yet?

---

### Post by sputnikkk on 2008-07-16
Bump for a newb interested in this working as well

---

### Post by mkeuter on 2008-08-02
Remove the line from modules section in your xorg.conf

**Load mga_hal**

after this you have to add this in the Section "ServerFlags" 

**Option "IgnoreABI" "True"**

to get past the next error

And all should be fine.

this info can be found on **[http://forum.tuxx-home.at/viewtopic.php?f=10&t=78](http://forum.tuxx-home.at/viewtopic.php?f=10&t=78)**

---

