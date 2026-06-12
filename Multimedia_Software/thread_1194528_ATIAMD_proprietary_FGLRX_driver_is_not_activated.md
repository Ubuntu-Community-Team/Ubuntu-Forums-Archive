---
title: "ATI/AMD proprietary FGLRX driver is not activated"
date: 2009-06-22
forum: Multimedia Software
---

### Post by xtraspecialj on 2009-06-22
This may be somewhere else in the thread, and I saw some issues pretty similar to this, but not quite the same.  Plus, the solutions given aren't working for me.  When I go to the Hardware Drivers section, it lists the ATI/AMD FGLRX driver as not activated.  I click on the green Activate button in the bottom right, it downloads and installs it, but it remains not activated.  I rebooted the machine and still nothing.  So, I opened a CLI and did it manually, and it says I already have the newest version.  I know that, but why isn't it activated.    I have a Asus A7n8x-E mother board with an ATI AGP 8x X1650 pro card.  I would like to activate this as my video playback really stinks.  Oh yeah, I'm running 8.10 by the way.

---

### Post by Melcar on 2009-06-22
That card isn't supported anymore by the drivers.  Last driver to support that card is 9.3 and Jaunty ships with 9.4.  You need to switch to the open source drivers.  
You have two choices; radeon and radeonhd.  The easiest thing to do is use radeon since Ubuntu already ships with it by default.  Simply open up your /etc/X11/xorg.conf file for editing, find the *Device* section, and add the following line:

```
Driver   "radeon"
```

Save and reboot.

Edit:  Saw you're on 8.10.  Scratch that then.  With Intrepid you should still be able to install the driver.  Best way to do it is to install it yourself:

[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")

Just remember to download the 9.3 drivers instead.

---

