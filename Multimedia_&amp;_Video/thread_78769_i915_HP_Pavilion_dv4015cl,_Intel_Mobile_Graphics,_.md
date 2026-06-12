---
title: "i915 HP Pavilion dv4015cl, Intel Mobile Graphics, performance slow"
date: 2005-10-18
forum: Multimedia &amp; Video
---

### Post by musb on 2005-10-18
Hi all,

     I have a Intel Mobile Graphics (i915) and while using ubuntu 5.04 it work fine, 3D acceleration work fine. After upgrade to 5.10 it work (dri work too), but performance slow.

     Anyone know why?

     Thanks

---

### Post by shof2k on 2005-10-22
I'm using Intel 845G graphics chipset and have similar problems.  I've downloaded the latest i810 and common modules from [http://dri.freedesktop.org/snapshots/](http://dri.freedesktop.org/snapshots/).

Installing these gives direct rendering but glxgears is no faster.  Doing this on Hoary gave ~700 fps.  I would love to have this on Breezy.

Any ideas on tuning the graphics here?

---Edit----
Just read [http://ubuntuforums.org/showthread.php?t=75973](http://ubuntuforums.org/showthread.php?t=75973).  Using glxgears -printfps shows 700fps.  Looks like the animation is just slow.  So install the above modules and that should help :)
---Edit---

---

