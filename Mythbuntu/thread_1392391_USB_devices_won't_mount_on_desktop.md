---
title: "USB devices won't mount on desktop"
date: 2010-01-28
forum: Mythbuntu
---

### Post by mrbadmood on 2010-01-28
I've set up my mythbuntu box and just need to start importing things to it as I cannot cable it up to my service yet. I have a number of movies and songs on USB devices on FAT32 and NTFS partitions but when I plug them in, they don't seem to be recognized. Not knowing the CLI, I keyed in MOUNT, but didn't show me anything. If I take these same devices over to my lappy running 9.10 with GNOME, they are automounted and show on the desktop. Since the mythbox runs XFCE, I guess that's part of the reason. How do I get mythbuntu to recognize and mount USB devices?

---

### Post by laffinet on 2010-01-28
Open Thunar (the xfce file manager), go to preferences, advanced.

Go to the "storage" tab, make sure the "mount removable drives when hotplugged" and "mount removable media when hotplugged" boxes are ticked.

Also make sure that the "thunar-volman" package is installed on your system.

---

