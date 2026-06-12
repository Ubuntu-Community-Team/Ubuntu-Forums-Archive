---
title: "will RT linux kernel improve mythtv performance?"
date: 2008-12-14
forum: Mythbuntu
---

### Post by hardyn on 2008-12-14
is myth coded in such a way where the linux RT kernel may help some?  I find it kinda sluggish.

AMD x64-3400 (754)
1.25GB RAM
750GB HDD
Embedded Nvidia 6100 with binary drivers
Mythbuntu 8.04
Hauppage PVR-150

I guess more ram, or hopped up video card is the next logical step, but it involves spending money; already too much has been spent on this toy :(

Thanks for any help.

---

### Post by hardyn on 2008-12-15
56 views and nothing, i guess is have stumped the panel. :)  i have googled around and have not found anything either; there is some mention of a realtime process myth is using but no mention of RT kernel.

It seems to me that it is something that would benefit from an RT kernel and some thread priority?  comments, questions? :)

thanks for all your help anyway.

---

### Post by ian dobson on 2008-12-15
Hi,

Don't think RT kernel would help MythTV much, unless the code has been written to use it.

One thing to try is set the suid bit for mythfrontend with something like:-

> 
To allow the video playback thread to be scheduled higher in the priority list than normal, we can set the SUID root bit on mythfrontend: 
chmod +s /usr/bin/mythfrontend


Regards
Ian Dobson

---

