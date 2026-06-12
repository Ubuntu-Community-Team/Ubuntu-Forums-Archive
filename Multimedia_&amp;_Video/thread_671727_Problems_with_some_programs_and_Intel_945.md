---
title: "Problems with some programs and Intel 945"
date: 2008-01-18
forum: Multimedia &amp; Video
---

### Post by Djalmahal on 2008-01-18
Hi,

i use Ubuntu now for 2 weeks, there are still some issues, one of them being that some programs, most notable Google Earth flicker a lot. I have an Intel 945 Graphic Card (1200*800), the driver is 

Intel - Experimental Modesetting Driver

I tried to change the driver to intel 945, screen blanked out, in some thread i read intel 810 would work, screen blanked out again.

Also the program 915resolution was mentioned but i don't know how to use it.

So, how do i get the flickering away. Also if i open a window in Google Earth (like of a picture are a wikipedia page concerning the place), the window and GoogleEarth seem to compete which one is on top.

Any ideas?

THanks
Andreas

---

### Post by tgalati4 on 2008-01-18
I have a 945 chipset and googleearth runs smooth.  Perhaps setting your video memory in BIOS to maximum.  Mine is set to 224 MB of shared video RAM.  Without doing that, the OS has to swap video memory which could cause flickering.

I have two modules loaded automatically:

i915                   25856  2 
drm                    83348  3 i915

I also use the experimental Intel modesetting driver.  I'm running Linux Mint 4 XFCE and it runs compiz and all the effects (that I have tried so far) fine.

---

### Post by Djalmahal on 2008-01-19
Ok, where do i change the BIOS Memery, right when it boot up with F12?

What does it mean, you have 2 modules loaded?

Thanks for the clarification.

ANdreas

---

