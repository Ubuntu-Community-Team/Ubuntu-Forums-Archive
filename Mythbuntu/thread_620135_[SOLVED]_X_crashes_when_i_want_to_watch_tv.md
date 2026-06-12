---
title: "[SOLVED] X crashes when i want to watch tv"
date: 2007-11-22
forum: Mythbuntu
---

### Post by Benthe1st on 2007-11-22
Hi everyone!

I have an Nvidia Geforce Ti4200, i've enabled restricted drivers, so nvidia-glx installed. I've also installed xserver-xgl package, because other way i dont have window borders in compiz. I have problem with mythbuntu. I have installed it on an existing ubuntu istallation ( so primarybackend, frontend & regular desktop combination). It worked fine for a while, but after installing xserver-xgl, i start mythtv frontend and trying watch tv X crashes an logs me out. I've removed (with purge) xserver-xgl, but the problem remained. The only way i can watch tv if i disable restricted drivers. Anyone any idea how i can make mythtv work when re.driv. are enabled?

---

### Post by Benthe1st on 2007-11-22
I was able to solve it. I deleted xserver-xgl, and didn't remove libglitz-glx1 and libglitz1 (they were automatically installed with xserver-xgl). Now everything works fine. (How can i mark the topic solved? :) )

---

