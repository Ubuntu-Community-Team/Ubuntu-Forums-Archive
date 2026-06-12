---
title: "xorg, nvidia, screen flashing black!"
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by supirman on 2006-06-06
Well, I've been running dapper devel versions for a few months, which I upgraded from 5.10.  I've not had any issues with xorg or the the nvidia drivers until yesterday.  All of a sudden, my screen kept shutting off and then coming back on anytime a new window opened or if I moved a window.  It was to the point where I couldn't do anything at all as the screen was almost continually black.

I'm running dual heads off my nvidia geforce fx 5200 and have not had any problems until something went wrong yesterday.  I don't recall performing any updates yesterday, though I may have as I hardly pay attention to them.  I then booted into console mode and tried uninstalling/reinstalling the restricted-modules and the nvidia driver to no avail.  GDM would come up as a black screen with a thin gray bar at the top and then my entire system was locked up.  I couldn't even Ctrl-Alt-F1 or Ctrl-Alt-Bksp.  

So, I've reinstalled Dapper and installed nvidia-glx, linux-restricted-modules-`uname -r`, etc and copied my old xorg.conf for dual heads back over from my network share and I'm getting the same dead screen on GDM startup.  The screen flashing is gone, but now I can't even log in when I try to use the nvidia driver, I'm forced to us nv and only one of my monitors.

Does anybody have any idea what the heck could have happened so suddenly, or how to get it working again?  The normoul routes seem not to be working.

Thanks,
Bobby

---

### Post by darkknight209 on 2006-07-18
I think it may be you card, but could you post your .xorg.conf

---

### Post by supirman on 2006-07-18
Thanks for the reply.  It was, in fact, my card.  I put the card into a different pc with the same result.  I bought a new card and all is well.

Thanks.

---

### Post by darkknight209 on 2006-07-18
Your welcome. I had a similar issue a while back and turned out soem how it was dammaged. Sadly i couldd find no cheap repair for it. $ all gone.

---

