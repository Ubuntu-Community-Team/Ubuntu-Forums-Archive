---
title: "How does xorg / videodriver work in the new ubuntu8.04"
date: 2008-08-14
forum: Multimedia Software
---

### Post by pietjanjaap on 2008-08-14
How does xorg.conf / videodriver work in the new ubuntu 8.04
Does someone have a link or explain.

In de xorg.conf is little info in the file, but in what file is the info now.
The xorg.conf file you can still change the grafic settings(size window), but how does this work with the new place/file where the info over the grafic cards is.

fix x in de recovery mode, here you can let ubuntu autodetect the videocard and monitor.

What other file does ubuntu use?

---

### Post by prshah on 2008-08-14
> **pietjanjaap said:**
> How does xorg.conf / videodriver work in the new ubuntu 8.04

The xorg.conf file is gradually being phased out; as a first step, graphics information is removed from it, and a lot more auto-detection is relied on. Hardy will respect settings in xorg.conf currently, but that may not hold true for future releases.

If you know what changes you want to make, you can manually edit the xorg.conf and restart X for the changes to take effect. The better way is: Press Alt+F2, give the command ```
gksudo diskplayconfig-gtk
``` and make changes there. Changes here are dynamic; they take effect immediately without the need for a restart; except for multiple monitors (currently).

---

### Post by pietjanjaap on 2008-08-14
Bump, 
Somebody more info, or a website?

---

### Post by markbuntu on 2008-08-14
xorg is moving to a total automatic detection system for video. There is no xorg.conf in Intrepid for example. Instead xorg automatically detects the video card and loads the driver for it and the default configuration for the driver and the monitor. Configuration is now done in the driver through its own configuration application.

If you want to get real technical about it, you can visit the xorg website. Try a google search for xorg.

---

