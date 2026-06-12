---
title: "TV Boots Up To &quot;too large&quot; Desktop"
date: 2009-03-08
forum: Mythbuntu
---

### Post by dsbw on 2009-03-08
Hi, gang--

Got a persistent problem with my MythTV box. It boots up with a desktop area of (I think) 1920x1080 but the actual resolution is set to 1280x720, so that I get a moving field over the desktop.

So, when I first boot, I have to use a mouse attached to the system to set the screen to the upper left. The same mouse of course can cause problems later if it's moved to the right or down. 

One curious side-effect of this is that if you go to the exit-out screen ("Do you really want to exit MythTV?") neither "No" nor "Yes, Exit now" are selected, meaning you have to go in with the keyboard or mouse again to select either.

If I set either 1280x720 or 1920x1080 in the NVidia X Server settings screen, the problem goes away, but only till I reboot again. Saving doesn't actually fix the problem.

Ideas?

---

### Post by newlinux on 2009-03-09
when you make the change in nvidia-settings, are you running it with sudo? If so what you might want to do is make a backup of your current /etc/X11/xorg.conf and while running nvidia with root priveleges get the settings how you want and select save settings to xorg.conf (somewhere in there). then it should work when you reboot. I had a similar problem before and this fixed. Problem was some settings in my old xorg.conf needed to be manually added back in the nvidia-settings generated one - this is why I recommend you back it up first...

---

### Post by dsbw on 2009-03-09
Thanks, I'll give this a try....

---

### Post by dsbw on 2009-03-14
Thanks, nl, that worked!

---

