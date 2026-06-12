---
title: "reaching 1024x768 with a capable but unrecognised (&quot;uncapable&quot;) monitor"
date: 2009-03-04
forum: Multimedia Software
---

### Post by nagymancs on 2009-03-04
_How to Setup unrecognized monitors? reaching 1024x768 when it's not available!_

the HW: 1600xp,512ddr@333,nv15 mx200, and an old (at least 15yo) Amaga monitor capable of 1024x768@60hz
sw choice: _xubuntu ibex /w xfce_

after setup it **installed** itself at 800x600 resolution **without recignizing the monitor** itself
-->at **gnome-control-center** \ **screen resolution** it shows the monitor as *unknown*, therefor the highest selectable resolution is 800x600

when I accepted it's offer from the docking tray to **install** the **nvidia binaries **to accelerate the render the available resolutions went down to only 2 resolutions: 640x480 and 320x240

so _I deselected their use_, though it installed and run without any errors

after this I marked for installation and tested every package that **synaptic** and **gnome-app-install** offered wich contained the: _monitor, resolution, display, or screen_ keywords and by description seemed relevant to my problem

all offered only the same set of resolutions that the gnome resolution setting screen showed



so my guess is the problem lies within a config file wich defines the monitor type, and specs

in other threads with resolution issues I saw **displayconfig-gtk** command

in the first couple of days it run at my computer (at least it boosted the cpu usage percent), but no window ever showed up, nor appeared any "command not found" error in the console..

since then, some package must have taken it with itself because it does come up with the "command not found" no matter the privileges of the running user

and i can't seem to find it in any package.. 



wich package is **displayconfig-gtk** in?

+wich command or application is responsible under xubuntu _to offer a list of available monitor types, or specs_? ?:

---

