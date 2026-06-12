---
title: "Intrepid Ibex ATi All-in-wonder Radeon 8500 + Acer X193W"
date: 2008-11-26
forum: Multimedia Software
---

### Post by Kopachris on 2008-11-26
It doesn't work.  The main problem is that it won't detect the display.  System>Preferences>Screen Resolution shows 1280x1024, 1024x768, 800x600, and 640x480.  Or, that was the problem.  I think I found the solution to *that* somewhere, but that was after I changed the resolution to 1024x768 from 1280x1024.  Now the screen is a bunch of weird diagonal stripes.  I've tried changing xorg.conf, but that doesn't do anything.  Now Ubuntu starts up in "low-graphics mode", reconfigures the screen/whatever and goes to the normal login screen which takes me to diagonal stripe mode again.  How do I get back to 1280x1024 so I can at least use my computer?  

I should be getting a new video card (ATi Radeon X1650 IceQ (well, MSI, actually)) later this week.

(Sorry if my post is a little non-coherent.  Ask me questions and I'll try to answer them.  I just didn't know what information to include.)

---

### Post by Jive Turkey on 2008-11-26
For out of the box goodness I would reccomend an nvidia card.  For now however, I would go to your xorg.conf and in the comments it should mention the command:```
  sudo dpkg-reconfigure -phigh xserver-xorg
```

to use that, boot, at the login screen press ctrl+alt+f2 log in and run that command.  In my experience w/ a radeon9800 card the restricted driver manager never worked for me, there is a very good wiki for the proprietary driver with step by step instructions that are easy to follow:

[http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu")

---

### Post by Kopachris on 2008-11-26
> **Jive Turkey said:**
> For out of the box goodness I would reccomend an nvidia card.  For now however, I would go to your xorg.conf and in the comments it should mention the command:```
  sudo dpkg-reconfigure -phigh xserver-xorg
```to use that, boot, at the login screen press ctrl+alt+f2 log in and run that command.  In my experience w/ a radeon9800 card the restricted driver manager never worked for me, there is a very good wiki for the proprietary driver with step by step instructions that are easy to follow:

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
I already tried to reconfigure xserver-xorg.  It didn't make any difference.:(

---

### Post by Kopachris on 2008-11-29
UPDATE:
Hitting F6 at the LiveCD menu, taking out the "-- " and adding "acpi=off" allowed it to boot and pick up the correct resolution.  I'm going to try to reinstall it later today.  I think the problem was that booting the LiveCD in safe graphics mode caused it to install it so that the default mode was safe graphics mode, so it only used default resolutions, etc.

---

