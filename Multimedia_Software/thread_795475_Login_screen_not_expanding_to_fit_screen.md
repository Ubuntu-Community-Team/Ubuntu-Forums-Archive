---
title: "Login screen not expanding to fit screen"
date: 2008-05-15
forum: Multimedia Software
---

### Post by kcackler on 2008-05-15
So, my fiancee and myself both have switched to Ubuntu for home use.  Our gateway laptops, which shipped with Vista, were driving us crazy with the issues.  The only issue we've got is that the login screen doesn't expand to fit our screens.  Instead, there is space left to the right of the screen and the bottom of it.  Where do we need to go to fix this small, but irritating issue (Having a white login screen with the Ubuntu brown on the sides is not horribly pleasing to the eys) :lolflag:

Thanks in advance.

Kevin

---

### Post by Toadmund on 2008-05-15
Go to System->Admin->hardware Drivers, and enable the proprietary drivers.

Your welcome, in advance.

---

### Post by kcackler on 2008-05-15
Thanks for the attempt, but that was actually the first thing I tried.  There aren't any proprietary drivers in use on the systems, according to that dialog.

Kevin

---

### Post by kcackler on 2008-05-15
In a related issue, the application bar in gnome also isn't extneding to the full screen width.  The main system bar is, but the other isn't.  I'm attaching a screenshot here.

You'll see the bar across the top isn't the full width, but the bar at the bottom does.

Kevin

---

### Post by Toadmund on 2008-05-15
That's a driver issue, I guess you will have to install your driver manually, if the 'hardware drivers' GUI can't enable it.
What is your graphics card?

---

### Post by kcackler on 2008-05-15
How can I find out what the graphics card is?  Gateway's description for the video driver is

 Intel Video Driver Version: 7.14.10.1283

Kevin

---

### Post by kcackler on 2008-05-15
Got it figured out.  Turns out the external display was overlapping the main laptop display, thereby causing the bars to cut off.  By moving the external display below the main display in the appearance menu, the bars are now expanding to full width.

**Seems I spoke too soon...I'm still experiencing the same issue.  I think it has something to do with the external VGA, but so far, my attempts to fix it have been useless.**

---

### Post by kcackler on 2008-05-17
*BUMP*

We would really like to sort this issue out somehow.  I'm fine with compiling drivers and editing configuration files, but I've got no idea where to look for the correct drivers.

---

### Post by kcackler on 2008-05-17
Apparently both of our laptops use an Intel chipset, which is supposed to be pretty tightly integrated into Linux.  Does anyone have any ideas for us?

Kevin

---

### Post by kcackler on 2008-05-18
I've now managed to drop my resolution down to 800x600.  Using the screen resolution dialog, I'm not able to increase that resolution to anything else...

Any ideas or help are VERY much appreciated.  I believe both of our chipsets are the Intel 945

Kevin

---

### Post by ekow on 2008-09-02
I have a Gateway laptop as well (MT6723) and I experienced all of the same glitches you are.  I managed to fix the panel problem by going into the Screen Resolution menu.  For me at least, it was showing two different displays, one called Laptop 15", and another called Unknown.  I simply set the resolution of the Unknown display to "off," then set the other to my optimal res, upon application the upper panel finally expanded the full width of the screen.

As for the login screen, I still have not been able to find a fix.  People continuously diagnose it as a driver problem, though I'm certain it isn't, the panel glitch wasn't.  Tell me if that helps, hope it does ^^

---

