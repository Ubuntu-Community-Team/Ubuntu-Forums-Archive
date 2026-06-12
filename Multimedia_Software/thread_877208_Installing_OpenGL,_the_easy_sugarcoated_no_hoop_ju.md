---
title: "Installing OpenGL, the easy sugarcoated no hoop jumping method"
date: 2008-08-01
forum: Multimedia Software
---

### Post by jukingeo on 2008-08-01
Hello all,

I am pretty much new to Ubuntu and Linux in general.  I am looking for the EASIEST, sugarcoated non-hoop jumping method to get openGL to work on my machine.

This is what I have on my machine:

Nvidia GeForce 5200FX

This is what I tried thusfar:

1) Synaptic--I tried a couple choices here, but there are DOZENS to choose from.  I tried glx-legacy, glx-new, glx-legacy-envy...all to no avail.

2) Searched here in Ubuntu Forms.  Most tutorials were outdated and seemed to be aimed at older versions of Ubuntu.  Other newer tuts seemed to have a lot of hoop jumping.  I am looking for the fastest, easiest way possible.

Any advise/suggestions appreciated.

Thanx,
Geo

---

### Post by jukingeo on 2008-08-06
Bump,

Anybody? Bueller?  Any assistance would be appreciated.

Thank You,

Geo

---

### Post by Melcar on 2008-08-06
Just install your graphics card's drivers.  Use either the restricted modules (System>Administration>Hardware Drivers) or [Envy]("http://albertomilone.com/nvidia_scripts1.html").

---

### Post by jukingeo on 2008-08-07
> **Melcar said:**
> Just install your graphics card's drivers.  Use either the restricted modules (System>Administration>Hardware Drivers) or [Envy]("http://albertomilone.com/nvidia_scripts1.html").

Hello,

Fed up with my problem, I blasted Ubuntu Studio yesterday and just reinstalled it.  Anyway, this time around I noticed a wee little icon shaped like a pc-card in the lower right hand corner of my taskbar.  I decided to click on it and low and behold it was a setting to enable accelerated graphics for my Nvidia card.  It said to select it for 3d graphics in applications and games.  So naturally I did so.  I did a mandatory reboot and everything seems to be OK.  I still have yet to reinstall my 3D applications, but I did verify that the "enabled" check mark for my card is in place.

So I am not sure if anyone noticed this icon before.   I know that I didn't notice it before.  Perhaps it is a new update.  But hopefully if it is working right, that would probably be the best sugarcoated, no hoop jumping method for 3d acceleration I have ever seen for Linux.

I will report back if I have any further problems.  But my guess is that if you have an Nvidia video card, Ubuntu (Studio) and you have completely updated the system, you should have this icon as well.  Apparently someone has been listening to the many problems people are having to get accelerated graphics to work with the nv restricted drivers.

So that seemed to be a nice discovery.

Geo

---

