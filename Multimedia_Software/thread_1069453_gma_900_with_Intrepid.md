---
title: "gma 900 with Intrepid"
date: 2009-02-14
forum: Multimedia Software
---

### Post by itchyfinger on 2009-02-14
I haven't found this problem so here goes.  I am installing Intrepid on a machine with a GMA 900 Intel card.  It has a strange problem.  I can see the screen it does not go black.  My problem is that the image is not taking up the whole monitor (the sides are squeezed in).  The whole image is there, and when I change resolution it changes the amount of screen used.  From my estimation, the proper drivers are not installed.  It wouldn't be such a problem, but I'm setting this up for a friend to convince them to go linux and set it up for dual boot with XP, until they are sold on it.

---

### Post by densou on 2009-02-14
> **itchyfinger said:**
> I haven't found this problem so here goes.  I am installing Intrepid on a machine with a GMA 900 Intel card.  It has a strange problem.  I can see the screen it does not go black.  My problem is that the image is not taking up the whole monitor (the sides are squeezed in).  The whole image is there, and when I change resolution it changes the amount of screen used.  From my estimation, the proper drivers are not installed.  It wouldn't be such a problem, but I'm setting this up for a friend to convince them to go linux and set it up for dual boot with XP, until they are sold on it.

Intrepid has issues when auto-detecting GMA cards, I tried openSuse 11.1 and it worked out-of-the-box :popcorn:

however if you need to fix Ubuntu look at your xorg.conf
{ open a terminal window, digit: *sudo gedit /etc/X11/xorg.conf* }

these two section should appear like this:

```
Section "Device"
        Identifier 	"intel"
        Driver     	"intel"
EndSection

Section "Screen"
        Identifier 	"Default Screen"
	Device 		"intel"
EndSection
```

or edit those lines :) (not risky for now)

---

