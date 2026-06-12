---
title: "Gamma Correction"
date: 2008-01-05
forum: Multimedia &amp; Video
---

### Post by Embryonic on 2008-01-05
I've been trying to figure this problem out on my own by searching but to no avail. I have a Gamma problem. <waits> Ok so, I use xgamma -gamma to fix the problem on the desktop. The REAL problem is that it does not save for the games when I try to play them, it seems like the game is using xgamma -gamma 1. Any ideas on how to fix this?  I would also like to note that I tried fixing it with the nVidia tool for gamma correction, but it has the same problem. Works on desktop but not in game. Any help would be awesome, Thanks everyone.

---

### Post by yabbadabbadont on 2008-01-05
Games generally have their own gamma setting somewhere in their settings menu.

You can also set your gamma using the "Gamma" option in the Monitor section of your /etc/X11/xorg.conf file.  

Just as an example:
```
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Option          "DPI"           "86 x 86"
        Gamma        0.75 0.75 0.75
EndSection
```

---

### Post by Embryonic on 2008-01-05
I didn't see a monitor section in my xorg.. I'm on my Windows drive right now, getting ready to play some DAoC but I will check when I'm done. Thanks!

---

### Post by Embryonic on 2008-01-05
This is what I have in the way of a monitor in my xorg. So do i just add in a gamma line to get it working?

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

---

### Post by yabbadabbadont on 2008-01-05
Yep.  Assuming that you know the correct gamma values to use.  By the way, you can specify the Red, Green, and Blue values separately (like my example), or you can just set one value and it will be used for all three.

Edit: "man xorg.conf" in a terminal window will yield a lot of information on the various options that can be used.

---

### Post by Embryonic on 2008-01-05
Great, That worked perfectly. Thank you!

---

