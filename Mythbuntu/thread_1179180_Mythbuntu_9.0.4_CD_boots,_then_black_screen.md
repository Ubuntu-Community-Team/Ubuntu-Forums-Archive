---
title: "Mythbuntu 9.0.4: CD boots, then black screen"
date: 2009-06-05
forum: Mythbuntu
---

### Post by mrdrc on 2009-06-05
I downloaded the 9.0.4 ISO image, burned a CD and booted from it. A progress bar appeared, then the Mythbuntu welcome screen popped up, providing options to try it out, install it, etc.

I clicked the first option (try it out). A progress bar appeared and I could hear the CD working away as it loaded the software. After a minute or so, the CD went quiet, and the screen went black. Neither keyboard nor mouse input had any effect.

I rebooted from the Mythbuntu CD, and clicked the second option (install it).  Same thing happened: a progress bar appeared, then a screenful of terminal output appeared. The installer looked like it was doing its thing, but after a second or so, the screen went black.

Could this be due to the fact that I have no monitor on the system?   My display is my TV, connected to the SVid-output on the graphics card.  The system presently has Gentoo+MythTV installed on it, and I've been using the TV-as-monitor forever, both running Gentoo, and when booted from a BartPE CD, a UBCD CD, and other utility CDs.

Perhaps the Mythbuntu CD explicitly disables video-out once it progresses past the Welcome screen? If so, is there any simple way to get the Mythbuntu CD to continue to use the video-out so I can get it to install itself?

Thanks.

---

### Post by DrWarm on 2009-06-05
I've heard success from people with this happening to try install in safe-mode in normal ubuntu. I can't remember all the options from the splash screen, but one of them might be similar to this for mythbuntu.

---

### Post by mrdrc on 2009-06-06
Alas, I don't know what is meant by "safe-mode" nor "normal ubuntu".  Which is to say that Ubuntu is pretty new to me.

---

### Post by DrWarm on 2009-06-07
Ah ok, I think that if you press F4 (it should say something like: Press F4 to select alternative start-up and installation modes) and then select: Safe graphics mode, it may help you.

---

### Post by mrdrc on 2009-06-07
Thank you, Dr.
I'll give it a try.

---

