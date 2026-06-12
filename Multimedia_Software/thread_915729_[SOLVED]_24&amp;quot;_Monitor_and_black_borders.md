---
title: "[SOLVED] 24&amp;quot; Monitor and black borders"
date: 2008-09-10
forum: Multimedia Software
---

### Post by soxs on 2008-09-10
I just got a new fancy w2408h widscreen24" tft from HP.

**Issue**
While booting the full size of the desktop is used, the bootsplash unleashes itself through the whole 1920x1200 pixel area.

As soon as I start gnome, I get a approximatly 3cm black border around my "Desktop".

I allready set desktop-resolution in my xorg.conf but this didn't matter, even a restart didn't change that blackborders.

Btw. it's connected via HDMI to my Radeon HD 4870. Does this matter?


Thx for any reply.

---

### Post by soxs on 2008-09-11
Note: The analog VGA cable works _without_ black borders.. any ideas why the f*** HDMI cable doesn't work? EDIT: No, it can't be broken, if it was, there would be no picture at all or a colour shifted one..

---

### Post by soxs on 2008-09-13
[http://www.avsforum.com/avs-vb/showthread.php?p=14472703](http://www.avsforum.com/avs-vb/showthread.php?p=14472703)
The problem seems to be catalyst / fglrx related.
the driver detects based on the did info sent by the monitor being connected to a TV and adding overscan (aka black borders) to it.

---

### Post by xc3RnbFO8P on 2008-09-13
Did you try 
atl+f2
gksudo displayconfig-gtk
and choose Generic
and resolution that your monitor supports.
I cant see your monitor on that list.

---

### Post by soxs on 2008-09-13
Adding this to /etc/X11/xorg.conf to the device section works:
```
Option      "ForceMonitors" "crt1"
Option      "EnableMonitor" "crt1,tmds2i"

```
[COLOR="SeaGreen"]**Issue Solved**[/COLOR]

---

### Post by soxs on 2008-09-13
> **Ringi said:**
> Did you try 
atl+f2
gksudo displayconfig-gtk
and choose Generic
and resolution that your monitor supports.
I cant see your monitor on that list.

I won't let displayconfig-gtk kill my xorg.conf again. I _HATE_ that "tool"...

And I know that HP w2408h supports 1920x1200 _without_ black borders

---

