---
title: "glxgears extreme difference between gnome-shell and unity."
date: 2011-04-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2011-04-23
when i was using the standard beta 2 with unity i got a glxgears score of about 60 fps, even if i used the ubuntu classic no effects i got the same score around 60 fps.

i have since reinstalled using the 11.04 mini.iso and installed the gnome-desktop-environment and then loaded the gnome 3 ppa and installed gnome-shell and within this environment is get glxgear scores of around 14000 fps. 

i have nvidia gtx460 gpu and using the nvidia-current drivers. 

any know why there is such a difference.

---

### Post by Ollboll on 2011-04-23
Sounds like vsync.

As far as I know compiz syncs by default to the refresh rate of your screeen, which for most people is 60 fps.

You can uncheck it in ccsm if you want to, doesn't remember where the checkbox it is though.

---

