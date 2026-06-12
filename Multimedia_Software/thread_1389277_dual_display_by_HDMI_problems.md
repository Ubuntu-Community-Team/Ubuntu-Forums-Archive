---
title: "dual display by HDMI problems"
date: 2010-01-24
forum: Multimedia Software
---

### Post by kwstas on 2010-01-24
hi,

having connected the HDMI cable from my acer 4810T(14") to the external monitor(22") by the system boot:
[INDENT]1. recognized my 2nd monitor but changed my laptop's resolution to one of 4:3.
2. shows as side by side screens. i can switch it manually but i'll need to have it mirror display by default if possible.
3. i get sound from laptop but not from tv. This one can also be manually switched from the sound configurations but i can get sound by one monitor at a time only.
4. when i disconnect the cable, my screen resolution is not auto-changing to the normal one.  
[/INDENT]so in case i try to connect the second monitor after the system is booted, i get all of the above plus another annoying thing...
since i get in the display configurations pannel, i can't get this icon/logo on the top left of the screen go away! it just sticks there even if i disconnect the cable!

guys, that's my problems!
i can live with them but i would also like to have my system as functional as possible.

i hope someone can guide me on this.

thanks

---

### Post by Tipoz on 2010-01-24
If you are using Gnome, have you tried the option in the menu under system/preferences/display? You can switch off the icon there.

If you want to do special things, you can use the  xrandr command. I scripted my preferences to switch on and of my dual monitor.

---

### Post by kwstas on 2010-01-24
> have you tried the option in the menu under system/preferences/display? You can switch off the icon there.i go there but i haven't figured out how to take it off..

i attached my "display" pannel


> I scripted my preferences to switch on and of my dual monitor.     i don't know how to do these..

---

### Post by kwstas on 2010-01-24
this icon

---

### Post by Tipoz on 2010-01-24
OK, did you try to activate "Show displays in panel" under panel icon, Apply. Then deactivate it and apply again. If that doesn't work i think you have to enter the configuration files (google for that).

Did you try xrandr?

---

### Post by kwstas on 2010-02-20
it seems that even though i don't have the "display settings" opened, it is running in system monitor!
so to get rid of that icon i just killed the "display settings" from there.

---

### Post by efflandt on 2010-02-20
If you connect a display after booting and want X to recognize it, or disconnect one and want your laptop display to go back to normal, and do not know how else to do it, just log out of X and log back in.

---

