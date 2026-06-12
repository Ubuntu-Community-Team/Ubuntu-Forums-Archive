---
title: "Turn off LVDS when laptop lid is closed"
date: 2008-10-07
forum: Multimedia Software
---

### Post by abc80 on 2008-10-07
Is it possible to turn off LVDS when the laptop lid is closed and turn it back on and turning off vga when its opened?

Something like this:

#when lid is closed
xrandr --output LVDS --off --output VGA --auto

#when its opened again
xrandr --output LVDS --auto --output VGA --off

Im having nightmares with the vga, i have to run the first command everytime i login to kde. Or else both vga monitor and LVDS is messed up (kde always resets the resolutions on booth monitors to 1024x768 with mirroring on)

Thanks in advance.

---

### Post by ne4ve on 2008-10-07
I'm pretty new to this myself but the other day I found a script called /etc/acpi/lid.sh. It appears to run some other scripts including lid.sh.pre and lid.sh.post which I imagine are custom actions you'd want to do. The folder the script looks in is /etc/acpi/local/ so I created the two scripts in there but it only ran lid.sh.pre. I'm not up on my shell scripting but it doesn't seem to get as far as running the lid.sh.post script.

I've been trying to do something similar. I was going to try to map fn + F4 (external monitor on my laptop) but couldn't get the keycode using the various methods but this sounds like a decent solution if I can figure out how to tell when the lid is opened again!

Let me know if you figure anything out. I'll do the same if I find out more.

---

