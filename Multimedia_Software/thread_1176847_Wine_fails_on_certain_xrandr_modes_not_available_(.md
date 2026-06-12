---
title: "Wine fails on certain xrandr modes not available (Jaunty)"
date: 2009-06-02
forum: Multimedia Software
---

### Post by Diskdoc on 2009-06-02
Since Jaunty, I can get something like this using Wine:

err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 800x600x16 @85! (XF86VidMode)

and there is no graphics when running the program. Apparently, xrandr and vidmode only offer 60hz resolutions. Also, I was forced to set DefaultDepth to 16 in xorg.conf to prevent complaints about not being able to switch from 32 to 16 bit.

Why does xrandr exclude modes with higher refresh rates? I admit, it would be smarter if the game/Wine would ask for 800x600x32 @60 instead.
Can I add the xrandr modes I wand to xorg.conf somehow?

/ Carl

---

### Post by Diskdoc on 2009-06-02
Alright..I got the program (game) to work in Wine doing the following:

In xorg.conf, in the "Screen" section, adding this:

DefaultDepth 16
SubSection "Display"
Modes   "1280x800@60" "800x600@85"
EndSubSection

AND

Doing "wine regedit" in a terminal, adding UseXRandR "n" to
machine\HKEY_CURRENT_USER\Software\Wine\X11 Driver\

But this isn't acceptable.. Why can't xrandr provide thee needed screenmode by default?

---

