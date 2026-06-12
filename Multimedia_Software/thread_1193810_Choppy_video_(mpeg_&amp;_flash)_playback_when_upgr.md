---
title: "Choppy video (mpeg &amp; flash) playback when upgraded to Jaunty from Gutsy"
date: 2009-06-21
forum: Multimedia Software
---

### Post by JasonOng on 2009-06-21
I have a touchscreen kiosk running on these specs 

- Gutsy Gibbon
- Via CX700/VX700 chipset
- Xorg "vesa" driver
- firefox running in kiosk mode 

Playing embedded videos (mpeg & flash) in firefox wasn't a problem until I upgraded to Jaunty which somehow causes video playback to be extremely choppy.

Anybody have any idea what has changed/wrong? I've tried many of the suggestions found in this forum to no avail and am considering downgrading to Hardy to see if it's better. Any such experiences in Hardy as well?

Any help would be greatly appreciated. Thanks!

---

### Post by walterdf00 on 2009-06-27
I'm seeing the same thing in jaunty.  I haven't tried it with anything earlier, though.

How do I know which driver is being used?  How do I change it?

This post, [http://ubuntuforums.org/showpost.php?p=4873860&postcount=4](http://ubuntuforums.org/showpost.php?p=4873860&postcount=4), says that there are accelerated drivers from VIA for our board now, too.

---

### Post by JasonOng on 2009-06-29
I managed to get acceptable video playback by doing the following:

**1. Use "openchrome" driver in vesa mode instead of "vesa"**

```
Section "InputDevice"
    Driver "openchrome"
    Option "VBEModes"  "boolean"
EndSection
```

**2. Use gnome-mplayer **

I've tried totem, mplayer & VLC, all of which gave me very high CPU load. Using gnome-mplayer reduced CPU dramatically.

---

