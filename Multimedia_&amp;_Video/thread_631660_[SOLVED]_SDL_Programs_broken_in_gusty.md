---
title: "[SOLVED] SDL Programs broken in gusty"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by Tuxoid on 2007-12-04
After installing gusty in October, all of my SDL-dependent programs will no longer load due to SDL not being able to detect my video card (i.e. 'no video device available' showing up in the terminal when I try to run any SDL program). I've tried to fix it for almost two months, now. I have tried configuring xorg.conf, resetting xorg.conf, running from the terminal, running in kde (don't know why I tried this), setting up SDL video driver variables, using different drivers for my video card, removing the 915Resolution package, completely removing all things SDL and re-installing them, and yelling at my laptop, telling it to work](*,). I use a 945 Intel Accelerated Graphics Controller, the i810 driver, and the 915Resolution mod. SDL programs worked fine in feisty, but don't even load on gusty.

---

### Post by jpeddicord on 2007-12-05
I'm not sure if you have tried this, but try using the intel driver instead of i810. You will get much better performance, and most likely this will fix the bug. :)

Jacob

---

### Post by Tuxoid on 2007-12-05
I switched the driver to intel, it works as well as the i810 driver. Unfortunately, I still can't load any SDL apps. If necessary, I can provide a list of all the SDL programs that are not working correctly.

---

### Post by Tuxoid on 2007-12-10
I upgraded from feisty to gusty. Could there be some SDL or X11 leftovers from feisty? Did they change any major SDL or X11 stuff for gusty? All I know is I have been searching for a solution on google, searching the ubuntu forums, seaching the libsdl main website, reading source code, and fiddling with, packages, environmental variables, and my xorg.conf for nearly two months trying to get my SDL apps to work.

---

### Post by Tuxoid on 2007-12-12
I saw that other users had the exact same video card working fine with SDL. yet, not a single SDL program will load for me.

---

### Post by Tuxoid on 2007-12-13
solved it. I finally solved. I installed SDL from source, and now, it works.

---

