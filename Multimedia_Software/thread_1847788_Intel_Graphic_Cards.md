---
title: "Intel Graphic Cards"
date: 2011-09-21
forum: Multimedia Software
---

### Post by ILikePizza555 on 2011-09-21
I have a a 15.6" ASUS laptop with the i3 that has a gpu in the processor. I was wondering if they're any drivers for that graphics card s, i can install compiz and run minecraft on my xubuntu set-up. I've already seen the intel linux drivers site, but i don't know how to compile them on my own. 

Any help?

---

### Post by BicyclerBoy on 2011-09-21
Should already be in use..

glxinfo | grep OpenGL

The default driver can be a bit old (safe), you can close to the latest source by using xorg-edgers launchpad ppa (higher risk).

If you want video decode (intel) h/w acceleration you need to look for VA-API libva etc..

---

### Post by FerroPower on 2011-09-22
go ahead and install the latest drivers from  xorg-edgers launchpad ppa
On the mainpage of the site there is instruction how to install the Latest Intel drivers once you have added the Xorg-edgers ppa (haven't come across any bug yet but it ROCKS !! )

I myself having Intel GM45 chipset. My graphics were slow previously but it got a new life now once I have installed the latest xorg-edgers drivers. 

No need to compile any drivers from Intel site. 

Good Luck !

---

