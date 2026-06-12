---
title: "intel 915GM and jaunty - SDVOB sync error?"
date: 2009-08-05
forum: Multimedia Software
---

### Post by meeotch on 2009-08-05
Since upgrading Hardy -> Jaunty, I can't seem to get xorg to run with *any* flavor of the intel driver.  (Though it works with vesa.)  I've got the Intel 915GM chipset:
```

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
```
I've tried downgrading to v2.4, like this [https://wiki.kubuntu.org/ReinhardTartler/X/RevertingIntelDriverTo2.4]("https://wiki.kubuntu.org/ReinhardTartler/X/RevertingIntelDriverTo2.4"), I've tried upgrading like this [http://ubuntuforums.org/showthread.php?t=1136738&highlight=jaunty+intel+915gm]("http://ubuntuforums.org/showthread.php?t=1136738&highlight=jaunty+intel+915gm") and this [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582"), but no love.

This is with a default xorg.conf, and with the appropriate additions as above.  The one constant is that all versions of the intel driver produce the following error from startx:
```
(EE) intel(0): First SDVOB output reported failure to sync
```

My Hardy xorg.conf was using 'Driver "i810"'.  However, if I attempt to use that driver with any of the xorg-video-intel packages above, I get "(EE) No devices detected."

After fighting with this for about 24 hours, I'm about ready to fall back to Hardy.  <sigh>  Ideas?

mitch

---

