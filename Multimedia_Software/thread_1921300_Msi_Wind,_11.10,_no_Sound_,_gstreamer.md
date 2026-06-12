---
title: "Msi Wind, 11.10, no Sound , gstreamer?"
date: 2012-02-06
forum: Multimedia Software
---

### Post by saqwe on 2012-02-06
Hi I've got (a gestreamer?) problem, no sound after update to 11.10

MSI Wind, with newest xubuntu and all updates

here's what a script gave me:

[http://www.alsa-project.org/db/?f=db8f3dc338a8db8097ec04697750ebbeb277ce05](http://www.alsa-project.org/db/?f=db8f3dc338a8db8097ec04697750ebbeb277ce05)

and a screenshot:

[http://data7.blog.de/media/562/6154562_f9cfa48192_l.png](http://data7.blog.de/media/562/6154562_f9cfa48192_l.png)

thank you

---

### Post by ajgreeny on 2012-02-06
More likely to be a pulseaudio problem I think.

For some reason pulseaudio often is set at install with some levels much too low, or even muted.  Check if you have pavucontrol installed and if not install it, then run pulseaudio volume control from the Sound & Video menu.  There you can set the configuration, both of the different devices and also the volumes of everything.

It may also be worth using ```
alsamixer
``` in terminal to check that the levels of outputs are not set too low.
Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

### Post by saqwe on 2012-02-08
thank you

yes the problem was pulseaduio-mixer was muted 

but i didnt see it

because hda-mixer was default

thanx again

cheers

---

