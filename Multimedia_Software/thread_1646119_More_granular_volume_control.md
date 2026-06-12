---
title: "More granular volume control"
date: 2010-12-15
forum: Multimedia Software
---

### Post by _glook on 2010-12-15
Howdy ya'll,

So I imagine this isn't a problem for most people (as was confirmed by my searches), but I would like to know if it is possible to have more granularity in the amount the volume goes up or down, like in the various Windows variants. I have a volume control dial on my Dell keyboard and what I notice is that each "click" on the volume control dial increases or decreases the volume about 2 or 3 times as much as I want the volume to actually change, so I have to go to the icon in the taskbar the adjust it more granularly.

So my question boils down to: can I change the amount the volume changes when I turn the volume control dial? I imagine the method would be the same for volume control buttons on most other keyboards.

Thank you for your time.

---

### Post by grumpus27 on 2011-04-03
Yours was the first post I found looking for a solution to this problem, I just found this in another thread:

gconftool-2 --type int --set /apps/gnome_settings_daemon/volume_step 2

where the integer at the end is from 1 to 100, the percentage of full scale movement resulting from a single click.
Works well for me with Ubuntu 10.04

---

### Post by rhrgbmx on 2011-05-27
Hey I also suffer from the same irritating problem however I am using gnome 3 does anybody gnome how I could possibly adjust the volume_step because its not in gconf-editor and that above command doesn't work for me, if I type it into the terminal nothing happens

---

