---
title: "Can't access &quot;System&gt;Preferences&gt;Screen Resolution&quot; option"
date: 2008-05-16
forum: Multimedia Software
---

### Post by awilli5 on 2008-05-16
I recently updated to Ubuntu 8.04, and after reading some forums on how to get my laptop screen to display on an external monitor, I've come to the conclusion that it's recommended to use "Xrandr GUI" instead of the "Screens and Graphics" tool. So my problem is that I can't access Xrandr GUI because you have to get to it through System>Preferences>Screen Resolution, and when I click on "Screen Resolution" I get the error message:

"The X Server does not support the XRandR extension. Runtime resolution changes to the display size are not available."

So then I read that you can access it through the terminal by typing:

"gnome-display-properties" but it gives me the same message.

Does it have something to do with my xorg.conf file? Please help, I feel like I've tried everything!

---

### Post by MaxCapacitor on 2008-05-17
If you have Nvidia proprietary drivers installed, try System>Administration>NVIDIA X Server Settings.

The command line equivalent is nvidia-settings.

---

### Post by awilli5 on 2008-05-17
I don't have nVidia though, I have Mobility Radeon X1300 (although I wish my laptop used nVidia). Another option would be to use the Catalyst Control Center, but I get an error message for that too about my ATI drivers.

---

### Post by MaxCapacitor on 2008-05-17
Scratch that, I'm such a noob, the xrandr extension library shows as being on my system according to the Synaptic Package Manager... dunno why inputting xrandr -v into my terminal returns back a "RandR extension missing" error.

You could try:
```
gksudo displayconfig-gtk
```
That worked for me on my old laptop with an ATI Rage Pro LT after I changed the display type.

---

### Post by awilli5 on 2008-05-17
Nah, I tried using that, but that only confuses the xorg.conf file, since on Ubuntu 8.04 it's no longer recommended to use that.

---

### Post by Seks on 2008-05-17
I get that too with dual monitors, so you got to do it the hard way :(

open up a terminal and type
> 
xrandr -s [desiredwidth]x[desiredheight]

---

### Post by Blastz on 2008-05-21
From mboisson about a similar problem

> I found the solution, with the xrandr command :

xrandr --output default --mode 1280x720

xrandr --output default --mode 1920x1080

There's also a lot of info on this command at [Thinkwiki]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2")

---

