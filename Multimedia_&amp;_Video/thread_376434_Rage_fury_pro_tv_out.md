---
title: "Rage fury pro tv out"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by truptrup on 2007-03-04
I was trying to get my Rage fury pro agp vivo card it has rage theater chip and is based on Rage 128 pro. working for tv out for my mythtv. I was looking at gatos but i am not sure if it is what i need. if so i dont know what to put in this command for xorg_prefix. anyone who has any ideas on getting this card to work would be great. i dont need tv in.

export XORG_PREFIX="/usr" (XORG_PREFIX/bin is where Xorg is located) what do i do for xorg_prefix. if it is "/usr/bin/xorg" it gives me an error of not being a valid identifier.

Here is my xorg.conf i have tried those drivers commented out and none seem to do the job. both the ati and r128 run glxgears just fine. vesa does do tv out.

---

