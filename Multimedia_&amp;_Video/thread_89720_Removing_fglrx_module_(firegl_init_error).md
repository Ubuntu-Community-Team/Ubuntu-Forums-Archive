---
title: "Removing fglrx module (firegl_init error)"
date: 2005-11-13
forum: Multimedia &amp; Video
---

### Post by dickohead on 2005-11-13
Good Evening,

I recently upgraded my graphics card from an ATI 9600se 128mb, to an NVidia 6600 256mb (good card!), but in doing so, I have been left with the ramins of my ATI drivers, which are still loading themselves as kernel modules at boot, I cannot remove the offending packages as they remove my xorg files aswell, and upon reinstalling xorg, fglrx installs again. How do I completely remove all ties to the fglrx module from xorg and my kernel? That way i can stop getting this erros when my system boots:
```
4294713-409000 fglrx: firegl_init *ERROR* Device Not Found
```
Which is a very correct error, the device is NOT found, so how do I stop the kernel from looking for it?
My xorg display is also quite laggy, especcialy with OpenGL screensavers etc, but the new tuxracer plays really well, DVD playback is jerky at best and resizing things can be a problem, I assume they are all to do with the conflicting nvidia and fglrx drivers?

---

### Post by dickohead on 2005-11-14
doesn't anyone have any pointers at all? It's quite annoying, because guild wars under cedega reports that my video card is unsupported, but allows me to continue anyway, with rather disapointing performance....

---

### Post by ffadmraven on 2006-03-11
Have you checked out the posting on the Nvidia drivers?  It may be a case that under your device listing, it is still showing the ATI card instead of the Nvidia card.  I don't remember the exact post, but it might help if you are still having problems.

---

