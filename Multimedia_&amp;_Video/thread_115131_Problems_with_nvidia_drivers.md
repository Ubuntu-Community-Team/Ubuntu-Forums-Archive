---
title: "Problems with nvidia drivers"
date: 2006-01-09
forum: Multimedia &amp; Video
---

### Post by Connollyir on 2006-01-09
I recently tried to install the nvidia-glx drivers to go with my Nvidia Geforce 7800GT and after following the instructions on the wiki and proceeded to change the driver setting  in the xserver conf file (I wouold tell you the exact file but I can't and you'll see why in a sec) from "versa" to "nvidia" and restarted xserver via ctrl-shft-backspace. xserver restarted and the new drivers came into effect: Nvidia logo and such with messed up resolution. 

I tried to change the screen resolution through desktop configuration, but my only options were 640x800 and some 320 setting. I didn't find any way to change the resolution through nvidia-settings so I went ahead and changed the xserver conf file back to the vesa driver setting and restarted xserver. 

At this point, restarting stopped - didn't become unresponsive, just stopped. I'll find out which process it stopped on and provide an update (I'm dual booting). 

I can boot with the Ubuntu "safemode" and it works so it has to be in the display drivers.

Any help?

-Ian

---

### Post by Connollyir on 2006-01-10
Ok well I fixed the boot problem, I accidentally spelled "vesa" "versa" and that did it. Still I've got issues with screen resolution when I use the nvidia-glx drivers.

-Ian

---

