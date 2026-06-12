---
title: "nvidia artifacts and lockups"
date: 2007-09-08
forum: Multimedia &amp; Video
---

### Post by afterburn188 on 2007-09-08
hello all,

I'm currently running ubuntu 7.04 (Feisty) and just installed a Nvidia 6200 card in my system.  The board ran fine in my other system under Gentoo.  Now however, as soon as I use the nvidia module as opposed to the nv module, I weird artifcats and slashes through my screen.  Upon attempting to run glxgears, X proceeds to consume 100% resources and then hard lock my system.  Mouse will still move but nothing else responds, SSH,telnet,serial term sessions all die.  I have heard of fixes to a similar lockup problem by disabling RenderAccel but this does nothing for me.  I've also removed glx and dri from my xorg.conf and ran with the nvidia module but the errors still occur.  I was able to take a screenshot of the problem in action:

[http://http://img353.imageshack.us/my.php?image=screenshot1df8.png](http://http://img353.imageshack.us/my.php?image=screenshot1df8.png)
[http://img508.imageshack.us/my.php?image=screenshot2pr4.png](http://img508.imageshack.us/my.php?image=screenshot2pr4.png)
[http://img146.imageshack.us/my.php?image=screenshotdz7.png](http://img146.imageshack.us/my.php?image=screenshotdz7.png)

These occur after I open something such as a menu or a terminal.  You'll also notice things in the system tray only show part of their icons.  I am thoroughly confused by this.  Xorg logs and kernel logs show no hints.  I should also note that i've tried multiple versions of the kernel and driver and even hand compiled multiple versions of each, same problem.  This makes me thing it is Xorg. Any ideas?

---

### Post by uranus124 on 2007-09-11
I also just intalled the nvidia 6200 TC video card and now the gui log in screen doesn't come.  X Windows (or something of that sort) comes up with an error and then pulls up a log in screen of just white text on black background, kinda like dos.  But it doesn't accept my credentials and i just can't log in.  Any ideas or help would be great.  I am running:

HP m7330n
Ubuntu 7.04 x64
Athlon x64 4200+


I do have 2 monitors plugged into the graphics card, is this part of the problem?

---

### Post by afterburn188 on 2007-09-11
I've had that problem with incorrectly installing the driver.  Let me guess the error message is on a blue screen saying X failed to start with an error like (EE) No device found or something?

---

### Post by uranus124 on 2007-09-12
Yeah, that sounds like it exactly.  It just started popping up after I plugged the nvidia 6200 card into the motherboard.  How do I add the proper drivers now?

---

### Post by afterburn188 on 2007-09-12
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nVidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nVidia_drivers_in_7.04)

Ironic how i'm solving someone elses problem in the thread i started looking for help in...

---

