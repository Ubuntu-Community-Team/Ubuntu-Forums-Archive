---
title: "How can I add screen resolutions to Gnome's &quot;Monitor Resolution Settings&quot; app?"
date: 2008-11-03
forum: Multimedia Software
---

### Post by kerryhall on 2008-11-03
How do I add resolutions to Gnome's "Monitor Resolution Settings" app without editing xorg.conf? I ask because it seems like I should be editing resolutions in one config file, not two different ones.

Thanks!

---

### Post by kerryhall on 2008-11-03
Ok, now I can't seem to add a resolution to the list no matter what I do. I have tried displayconfig-gtk as well as editing xorg.conf. I have no clue what to do. All I want to do is add the option of having 1680x1050

---

### Post by kerryhall on 2008-11-04
Bump

---

### Post by kerryhall on 2008-11-18
Bump.

---

### Post by kerryhall on 2008-12-02
Bump.

---

### Post by kerryhall on 2009-01-08
Bump.

---

### Post by ButtonMasher on 2009-01-10
I was having the same problem with my new Acer AL2216W widescreen monitor.  Your post reminded me about the 'sudo displayconfig-gtk' command.  I ran that command and then selected the correct monitor in the control panel.  After I logged out and then back in, I was able to select 1680x1050.  I hope this helps.

---

### Post by kerryhall on 2009-02-18
My monitor does not show up, autodetect does not detect the correct settings, and I have no idea how to manually enter the horiz and vert refresh rates. Also, I selected generic 1680 x 1050, but that didn't work either.

---

### Post by kerryhall on 2009-02-25
Bump.

---

### Post by kerryhall on 2009-03-03
Bump.

---

### Post by AndyCooll on 2009-03-07
You can try using the xrandr command as follows:
```
xrandr -q
xrandr --addmode HDMI-2 1440x900
xrandr --output HDMI-2 --mode 1440x900
```
The first line gives you information about your monitor. 
The second line then adds a resolution to your listing (in the above case adding 1440x900 to the HDMI-2 monitor settings, obviously you'll need to modify your monitor and screen resolution details accordingly).
The third line then changes your screen resolution to that new setting.

I have to admit this hasn't resolved the problem for me. It does do what I've mentioned above and it works great. The problem I've been having is that these settings don't seem to stick, so I have to repeat the above everytime I login.

:cool:

---

### Post by epictour on 2011-05-14
The following link explains how to make changes to xrandr and have them permanently applied at startup.

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

---

