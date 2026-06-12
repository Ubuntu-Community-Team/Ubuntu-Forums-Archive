---
title: "hdmi not working with sharp tv.........drivers needed????"
date: 2011-01-04
forum: Multimedia Software
---

### Post by newbie2222 on 2011-01-04
Im new to ubuntu and so far think its amazing but i cant seem to get my sharp tv connected to my compaq presario cq50. by hdmi

i followed this 

I connected the HDMI cable to my laptop  with the TV already on (my  laptop was on too). 2. Went to NVIDIA X  Server Settings, then to X  Server Display Configuration and on the  Display Tab I chose my TV  (Samsung) as the "model", then configure it  so that the TwinView mode  was switched on, then I changed the  resolution to 1920x1080, position:  absolute and then I checked the box  "Make this the primary display for  the X server" (I guess this is what I  was missing in the first place).
3. Clicked on Apply and then my TV started to show what I was doing on my laptop. 

my computers reading the tv but when i click apply its still blank and i lose my mouse and boarders on my computer

---

### Post by BicyclerBoy on 2011-01-04
Don't turn on twinview...
Don't use xinearama.

Configure as separate X screens. This allows independent modes etc.. 

The TV may need to be set to PC input mode to get just-scan, pixel mapping, no overscan.

This will allow use of RGB & YUV color space. (latest nvidia drivers).

---

