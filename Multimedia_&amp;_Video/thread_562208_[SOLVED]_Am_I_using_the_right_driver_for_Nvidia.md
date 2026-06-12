---
title: "[SOLVED] Am I using the right driver for Nvidia?"
date: 2007-09-28
forum: Multimedia &amp; Video
---

### Post by TheThinker on 2007-09-28
Hi everyone! A long time ago I got my Nvidia GeForce MX 4000 to work thanks to LifeToHymn and others who took the time to aid me in my time of need (gaming need that is). Anyway, I just realized something about the particular driver that I used from the Ubuntu repositories. Unless I'm mistaken, my graphics card is part of the Nvidia "Legacy" series but the problem is that I don't know if it's considered an old or new card according to my particular driver.

I'm currently using the Nvidia-GLX driver from the repos and it does mention being compatible with Legacy chipsets. What catches my attention is that the Nvidia-GLX-Legacy driver mentions the same thing, except it emphasizes old chipsets. 

The question is: Should I switch to Nvidia-GLX-Legacy in the repos or stick with the normal Nvidia-GLX?

So the only performance issue is that GNOME is slightly sluggish but that's about it. I have no way of telling whether my driver is holding it back or not.

Thanks to everyone for their input.

---

### Post by w4ett on 2007-09-28
You can try the specific legacy driver, but depending on the amount of VRam on your card, Gnome can be a bit sluggish.  Not to dis your current card by any means, but the MX440 is getting a bit long in the tooth.

---

### Post by TheThinker on 2007-10-01
I once read that the Nvidia drivers for Linux are known to have issues rendering in 2D. Could that be why Gnome is a little sluggish? My card's memory is 128MB and I figure it shouldn't be a VRAM issue. Runs 3D stuff fine, including Beryl. 

Thanks w4ett.

---

### Post by w4ett on 2007-10-01
> **TheThinker said:**
> I once read that the Nvidia drivers for Linux are known to have issues rendering in 2D. Could that be why Gnome is a little sluggish? My card's memory is 128MB and I figure it shouldn't be a VRAM issue. Runs 3D stuff fine, including Beryl. 

Thanks w4ett.

Well, if beryl and games are running ok, I'm not sure of where to go from here to address the 2d issue.  Can we get some system specs besides the gfx card (CPU & Memory).  Also are rou referring to rendering speed when talking about 2D?...like the amount of time to render a webpage, especially one that uses a number of Java applets?

---

### Post by TheThinker on 2007-10-01
I'm running on an E-machine Celeron D 2.8 Ghz processor (x186) with 750mb of RAM. Well, it doesn't have internet access yet but yes, I was referring to rendering speed.

For instance, when I play Starcraft using Wine the game menu is not animating smoothly. I think this is a common problem with the game, but I've noticed similar issues with other 2D games that are native to Windows using Wine. It could just be a problem with Wine, or that my graphics card  isn't being utilized properly.

---

### Post by w4ett on 2007-10-01
Yea..I would point my finger at wine first....You might want to draw a comparison between a game running under wine and one of the native linux games to check the difference...Apart from the gfx card (which is not that shabby), you system specs are more than adequate.

---

### Post by TheThinker on 2007-10-01
Oh, I have Linux 2D games on hand like Battle for Wesnoth and they run great so more than likely it's an issue with Wine and I have little to complain about. So, should I switch to the older driver (that is, the Nvidia-GLX-Legacy driver) or just keep the one I have? If I should,  will the performance be any better?

Thanks a bunch for your input w4ett:KS

---

### Post by w4ett on 2007-10-01
I'd stick with what you have now...the old adage applies:  "If it ain't broke, don't fix it".  I wouldn't worry about it until you decide to upgrade the video card.

---

### Post by TheThinker on 2007-10-02
Okalee Dokee. Thanks a lot!

---

