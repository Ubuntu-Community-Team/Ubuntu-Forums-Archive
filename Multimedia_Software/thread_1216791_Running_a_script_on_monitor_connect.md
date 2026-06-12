---
title: "Running a script on monitor connect?"
date: 2009-07-18
forum: Multimedia Software
---

### Post by DaVince21 on 2009-07-18
I have a netbook (Eee PC 701, to be exact), and I have a big VGA monitor which I usually have connected to it. Currently, behaviour of Ubuntu is less than optimal when I connect my external monitor: if I do this before boot I end up with two screens in 640x480, if I do it afterwards it's not even on. In either case I'll have to run a tool like lxrandr to turn off my first screen, turn on my second screen and set it to an appropiate resolution (usually 1440x900).

I was wondering if this could all be done automated, though, both on bootup and when I connect the monitor to my VGA port while the computer is on. Is there something I can do in xorg.conf for the bootup part?

I wouldn't mind running a script instead of having the autodetection, but I'm not savvy in regular xrandr commands in order to disable/enable screens with the command line. Assistance in this would be greatly appreciated. :)

---

### Post by kerry_s on 2009-07-18
plugging a monitor in while the computer is on is not safe, you could short out your vid card & end up with no displays.

---

### Post by DaVince21 on 2009-07-19
I doubt it - this is a laptop, and it's fairly common for people to actually do this. I don't think xrandr would suddenly detect the second external monitor while it's on if there was really such a dangerous issue.
Uh, anyway, I'd like some source on that.


So, rather than the autodetection (guess I'll try to write a script), how do I get the second monitor's screen resolution right when the PC / X starts?

---

### Post by kerry_s on 2009-07-19
> **DaVince21 said:**
> I doubt it - this is a laptop, and it's fairly common for people to actually do this. I don't think xrandr would suddenly detect the second external monitor while it's on if there was really such a dangerous issue.
Uh, anyway, I'd like some source on that.


So, rather than the autodetection (guess I'll try to write a script), how do I get the second monitor's screen resolution right when the PC / X starts?

i guess i'm wrong it looks like the vga is hotpluggable now, sorry.

maybe a keyboard shortcut to set the external monitor?

---

### Post by DaVince21 on 2009-12-16
Coming back to a really old post to mention that Xubuntu now automatically remembers your screen settings - it disables my internal monitor and enables my external monitor with the right resolution completely automatically now.

---

