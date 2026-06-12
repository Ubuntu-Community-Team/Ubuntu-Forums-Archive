---
title: "very small font in vlc menus"
date: 2010-01-24
forum: Multimedia Software
---

### Post by brplut40 on 2010-01-24
I am running mythbuntu 9.10 with all patches and updates. I open VLC from the menu on the desktop and the font is so small I cannot read the menus. I can read every other menu on all other programs, just not in VLC. Because of this I cannot configure my audio output device. I have gone into Applications -> settings -> Appearance and made sure the font size is set to 11. Is there anything else I can change to be able to read the menus in VLC?

---

### Post by mc4man on 2010-01-24
While the font size in vlc is fine here (ubuntu) you could try installing qt4 config and see what you can do.

At the very least the default gui, (gtk), should be changed, it's bugged and not too suitable. Cleanlooks is better.

```
sudo apt-get install qt4-qtconfig
```
(found in system - prefer.... - QT 4 Settings

---

### Post by brplut40 on 2010-01-30
After I installed qt4-qtconfig the font was still really small and I could not read it, even in qt4 settings. I clicked around enough to find the font size is the second tab from the left in qt4 settings and the point size is the third drop down menu. I changed this to something much larger, 20, clicked file from the menu and exit. It asked me if I wanted to save and I clicked yes. This solved my small font problem.

---

### Post by whittylp on 2010-02-04
It seems like the VLC menus are statically coded to require 96dpi (or is 100) screen resolution.  Try 
  xrandr --dpi 96
Then start VLC, the menus should be readable.

More on setting your DPI here:
[http://wiki.archlinux.org/index.php/...y_size_and_DPI]("http://wiki.archlinux.org/index.php/Xorg#Display_size_and_DPI")

See also this thread for its effect on certain menus within mythtv itself
[http://ubuntuforums.org/showthread.php?t=1374838](http://ubuntuforums.org/showthread.php?t=1374838)

---

