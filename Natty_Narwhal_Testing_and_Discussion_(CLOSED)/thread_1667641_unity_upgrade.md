---
title: "unity upgrade"
date: 2011-01-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by terry_gardener on 2011-01-15
I have just done upgrade and it removed 4 packages, 2 of which and unity recommends packages. 

unity-place-applications 
unity-place-files 
libunity0 
and libindicator1 

libindicator1 was replaced by libindicator2 

what are the others for. 

thanks

---

### Post by kyleabaker on 2011-01-15
I also upgraded, but I opted to keep those files. I'm not sure that all of the issues have been worked out now or not.

One thing that changed that is annoying to me is the slight opacity when your drag a window around..

[IMG]http://img705.imageshack.us/img705/6206/screenshot1bmn.png[/IMG]

Its not just in the title bar which is the most evident place, but the entire window when your dragging it around and it dramatically degrades performance. In fact, if I drag a window around at a normal speed, the cursor doesn't appear to be attached to the window at all, and instead the window follows a trail of where the cursor was.

I haven't enabled the restricted video drivers yet, but I think this should be performing so slowly for those of use using open source drivers, especially when this option is apparently enabled by default. How can I disable this?

---

### Post by terry_gardener on 2011-01-15
seems fine to me when moving windows around, though i am using the restricted nvidia-current drivers.

---

### Post by kyleabaker on 2011-01-15
> **terry_gardener said:**
> seems fine to me when moving windows around, though i am using the restricted nvidia-current drivers.

I typically use the restricted drivers around Beta/Final stages, but during alpha stages I always seem to have problems with restricted video drivers. Maybe its time I try reinstalling, thanks. ;)

---

### Post by coffeecat on 2011-01-15
> **kyleabaker said:**
> Its not just in the title bar which is the most evident place, but the entire window when your dragging it around and it dramatically degrades performance. In fact, if I drag a window around at a normal speed, the cursor doesn't appear to be attached to the window at all, and instead the window follows a trail of where the cursor was.

It's working OK for me with an ATI Radeon HD4350 and open source driver (desktop) and Intel Mobile 4 graphics (laptop). What graphics card do you have?

---

### Post by kyleabaker on 2011-01-15
Nvidia 7300le, should be plenty enough to handle this. I'm installing the restricted drivers now to try them though.

EDIT:
Works beautifully with the restricted drivers (as I expected it would). Now I just hope they don't bomb on me during my next update. :/

---

### Post by anders_c_ on 2011-01-15
The Move Window plugin in ccsm has a slider for opacity if you want to disable it.

---

### Post by kyleabaker on 2011-01-15
> **anders_c_ said:**
> The Move Window plugin in ccsm has a slider for opacity if you want to disable it.

Thanks I saw this and will likely adjust that setting if I go back to the open source driver. :D

---

