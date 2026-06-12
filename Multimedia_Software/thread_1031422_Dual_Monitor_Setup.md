---
title: "Dual Monitor Setup"
date: 2009-01-05
forum: Multimedia Software
---

### Post by phiberoptik on 2009-01-05
Okay, I have looked everywhere for this. Spent many hours investigating this issue and not found anything.

I have a Lenovo T61 with the Nvidia Quadro graphics card. Everything on this laptop works great when I am off the docking station but when I shut down and restart ON the docking station (with the lid closed) there is no graphics... 

Basically, I start up, see the BIOS screen on my right side monitor, am able to enter my encrypted drive password, see Ubuntu start up, but as soon as Gnome starts up, both my monitors lose input signal. 

I have to hard Shutdown cuz I cant see anything. If i undock,  and restart the laptop screen starts just fine. I have a screen resolution of 1200x800 and everything works again.

My docking station monitors are both 19" 4:3 and support 1280x1024 resolution.

I have installed the nvidia-glx and glx-new restricted drivers but that didn't help at all.

I am fairly new to Linux in general. Any help would be greatly appreciated!!!!

---

### Post by jmchardy on 2009-04-23
I have the same problem, but with a T60.

Docking Bay Type - 2504 (not a problem with the docking bay as I've tried others)
T60
Lenovo Monitor (but it's not that as I've tried many others).
Ubuntu 8.10 (with nothing but the standard updates as of today)
ATI Graphics (using the Generic Drivers, not ATI/AMD proprietary FLGRX (although, I should verify how they work))

I can start the Laptop up off the Docking station, Laptop Screen - Fine, I can plug in an External Monitor... that works fine.

I cannot put the laptop back on the docking bay, it doesn't recognise it, I can only see it if I boot.

I can start the laptop on the docking bay with NO EXTERNAL MONITOR (DMI or ANALOG).

I cannot start the laptop with an EXTERNAL DMI or ANALOG monitor plugged in with the laptop screen open, but I can 1/2 start it with it closed, but the XServer still closes the screen when you get past the Ubuntu Splash Screen. The entire screen is shut down, both external and internal (backlights go off on Laptop, and External says - No Signal).

I can start on the docking bay, or off the docking bay and plug in an external monitor once Ubuntu is live (i.e. logged in to the Gui).

When I take the laptop that has been booted off the Docking bay and place it on the Docking bay (on, not off) the monitor can be detected and used, but the USB devices cannot (Mouse-Keyboard).

I'm assuming there is a number of problems here. I'll continue the investigation, but if anyone has any hints?

---

### Post by SuperSonic4 on 2009-04-23
What happens if you load nvidia-settings as root? ```
gksu nvidia-settings
```

---

