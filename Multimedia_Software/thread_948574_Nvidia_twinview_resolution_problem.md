---
title: "Nvidia twinview resolution problem"
date: 2008-10-15
forum: Multimedia Software
---

### Post by sgtstadanko2 on 2008-10-15
Hey All,

I am running the nvidia driver and have been using twinview to span 2 monitors with the same desktop.  I rebooted today and when X started back my right monitor resolution is now set to 1024x768 while my left is 1280x1024 and I cannot figure out how to reset it back.  Nothing has changed in my xorg.conf at all. These are the exact same make/model monitors as well (HP L1706). I tried forcing it back with the nvidia-settings tool but that just produces a non-working config for me.

any ideas out there on how to fix this?

Thanks,
Bill

---

### Post by sgtstadanko2 on 2008-10-15
nevermind.  got a bit hasty there. fixed it myself by changing the xorg.conf from using nvidia-auto-select on the second monitor to manually 1280x1024.   Weird that auto-select stopped setting the rez.

Oh well

---

