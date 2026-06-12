---
title: "restarting Ubuntu causes NVidia driver settings to be lost"
date: 2008-03-08
forum: Multimedia &amp; Video
---

### Post by UberrrSauce on 2008-03-08
I recently installed Ubuntu Gutsy 7.10 64bit in an effort to get WINE up and running so I could try my hand at gaming in Linux.

I have an Inno3D GeForce 7300GT 512MB AGP graphics card and I installed the NVidia drivers for it, which worked fine. I could enable desktop effects, crank up my screen's resolution, and if I had some games working, I bet I would have been able to play those fine too.

I later restarted to finish installing the flash and Java plugins for FireFox (having to do the 32bit hack) but I was presented with a "low graphics mode" dialog upon reaching the welcome screen. I reinstalled the drivers and everything was working fine again, until I restarted once more, but now when I reinstall the drivers, the changes aren't even being made at all - before everything would work fine until I restarted, but now It refuses to work from the second I install the driver. What the hell is going on?!?!

This happened before with my AGP GeForce FX 5500 256MB but that card died a little while after I decided to ditch Ubuntu - I started to worry I would inflict harm to myself from the ******** I had to go through to troubleshoot the problem, which was never solved.

So please, I don't want to ditch Ubuntu again - I *really* want it to work this time! :(

And my head hurts :(

---

### Post by uberlube on 2008-03-08
What method did you use to install your drivers?

---

### Post by UberrrSauce on 2008-03-08
I manually downloaded the driver (GeForce 7 series, Linux, 64bit) from the NVidia website and exited the x server, then typed

```
cd Desktop
sudo sh NVIDIA-Linux-x86_64-169.12-pkg2.run
```

I then followed the prompts.

---

### Post by uberlube on 2008-03-08
Grab envy and install them with that. After it installs the driver it adds it to the boot process for you.

---

### Post by UberrrSauce on 2008-03-08
> **uberlube said:**
> Grab envy and install them with that. After it installs the driver it adds it to the boot process for you.
you're a legend.

:guitar:

THANKYOU SO MUCH!

---

### Post by uberlube on 2008-03-08
No prob dude, glad I could help! :)

---

