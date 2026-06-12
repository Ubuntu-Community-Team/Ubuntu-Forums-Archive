---
title: "Extend display to a second montior with new Thinkpad 520 with nvidia nvs 4200m"
date: 2011-05-24
forum: Multimedia Software
---

### Post by adjfac on 2011-05-24
I just got a bran-new T520 with nvidia nvs 4200m card. Finally got the official driver to work downloaded from nvidia's site, with optimus disabled from bios. So everything as far as video goes, it's working.

Now I need extend my display to a second monitor -- nvidia has this thing called twinview, after messing with it, i got it to work by modifying the xorg.conf file. But it seems like if even if the monitor isn't attached, ubuntu still thinks i got two displays unless i copy back the original xorg.conf. So does this mean every time I want to extend to a 2nd monitor I need to copy over a new xorg.conf file, reboot and then copy over the original xorg.conf (& reboot) when i am not using the 2nd monitor?

Also seems like if I am using nvidia x server settings -- the default ubuntu display setting won't work. It doesn't even detect a new monitor when one is attached from the GUI. 

Thoughts? Anyone out there running 11.04 on a laptop with a 2nd monitor?

---

