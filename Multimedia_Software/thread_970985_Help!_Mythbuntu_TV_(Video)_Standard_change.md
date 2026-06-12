---
title: "Help! Mythbuntu TV (Video) Standard change"
date: 2008-11-04
forum: Multimedia Software
---

### Post by TyTiger on 2008-11-04
Hi all, 
this is probably quite trivial to some, but my brains gone to sleep and im pressed for time.

Basically, i just finished re-installing Mythbuntu after a hard drive upgrade (last one was old and loud) and i was an idiot enough to select the wrong video standard for my TV. Instead of selecting PAL-B i set it as PAL-M and so the video is black and white.. :(

Does anybody know how to change it from PAL-M to PAL-B. 
Its an nVidia Geforce 4 MX 440 Graphics card, and the nVidia Utility is on there but it doesn't have any fields for drop down menus to change the Composite video standard like i'd hoped :(

Hope i get this fixed before i miss my film!

---

### Post by TyTiger on 2008-11-04
Bump
.

---

### Post by TyTiger on 2008-11-04
Ok, after a little thought  (dont mean to spam...) it occurred to me that this should be under the xorg.conf file under /etc/X11/

Yes it is, and says PAL-M where line: 

Option "TV Standard" "PAL-M" 

:lolflag:is in there, im going to go ahead and change that to PAL-B and restart the xserver see how it goes.

---

### Post by TyTiger on 2008-11-04
> **TyTiger said:**
> Ok, after a little thought  (dont mean to spam...) it occurred to me that this should be under the xorg.conf file under /etc/X11/

Yes it is, and says PAL-M where line: 

Option "TV Standard" "PAL-M" 

:lolflag:is in there, im going to go ahead and change that to PAL-B and restart the xserver see how it goes.

Yup :) That worked after saving the changes and Restarting X (Ctrl+Alt+Backspace)

---

