---
title: "xorg"
date: 2008-02-20
forum: Multimedia &amp; Video
---

### Post by supersai20 on 2008-02-20
Ok so here's the problem i have a nvida geforce mx 4000 graphics card so i tryed to install it and then gnome either dosent start up or xorg is configured beyond fixing i wanna know how to install my video card right
computer:dell optiplex gx 50

current video card:intel onboard video

monitor:dell E151FP

---

### Post by overdrank on 2008-02-20
> **supersai20 said:**
> Ok so here's the problem i have a nvida geforce mx 4000 graphics card so i tryed to install it and then gnome either dosent start up or xorg is configured beyond fixing i wanna know how to install my video card right
computer:dell optiplex gx 50

current video card:intel onboard video

monitor:dell E151FP

HI and welcome, Have you tried Envy to install the drivers? [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Also make sure then onboard graphics is disabled in bios.

---

### Post by supersai20 on 2008-04-20
so i disable on board BEFORE installing drivers with envy

---

### Post by overdrank on 2008-04-20
> **supersai20 said:**
> so i disable on board BEFORE installing drivers with envy

HI and yes you will need to make sure that it is disabled. Have you tried to reconfigure your xorg when you boot into ubuntu. when you reach the login screen use the keys ctrl, alt, F1 all at the same time and this will bring you to the command line. Login with user name and password and then enter this command 
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` and answer a few questions and when complete use the command to reboot ```
sudo reboot
``` Hope this helps and good luck!

---

