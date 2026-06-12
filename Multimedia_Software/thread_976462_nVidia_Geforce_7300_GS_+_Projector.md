---
title: "nVidia Geforce 7300 GS + Projector"
date: 2008-11-09
forum: Multimedia Software
---

### Post by realifeministries on 2008-11-09
Hey all,

I installed an nVidia Geforce 7300 GS on a box running Ubuntu Hardy and I'd like to use the S-video out to display a projector.  Ideally I'd like a Xinerama display but I'll settle for Twinview.  However at present I can't get either option to work.

I installed envyNG, and ran it, and my video drivers are properly configured (no issues at all setting it up, good job Alberto!).  I opened up nvidia-settings and this is what I've got:

[LIST]
[*]The TV output shows up when I have the wire plugged in.
[*]It is disabled
[*]When I "configure", I choose "Separate X Screen" and then check "Enable Xinerama"
[*]I save to my xorg.conf (no merge) and everything's successfully saved.  I've verified it by opening xorg.conf afterward.
[*]I restart GDM and it starts up fine, but only the primary screen ever displays.
[*]When I go back into nvidia-settings, it shows the TV out still connected
[*]If I attempt to set it up as TwinView, I get an error that says that the XRandR extension is required but not installed.
[/LIST]

Here's some stuff I think you might need.  if there's anything else, let me know.

**Contents of > lspci | grep VGA:**

02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7300 GS] (rev a1)

**My xorg.conf is attached as a .txt file.**

---

### Post by realifeministries on 2008-11-16
bump... no suggestions?  Could this be an issue with the card, or is it more likely to be a configuration problem?

---

### Post by cabinetman on 2008-12-12
I don't know if this will solve your problem or not. It worked getting my projector to work on vga. Enter this in terminal. Your resolution might be different.    

xrandr --output S-video-0 --mode 1024x768

xrandr -q    

will show you what you have connected

---

### Post by dnr101 on 2009-01-15
Not sure if this applies to the original problem, but I was trying to convince my machine to display on both the laptop display and an lcd projector (for .ppt's, etc) with minimal hassle and inconvenience. Here is the solution I came up with, I think it could be easily modded to suit your needs. I made two custom launchers on my bar that launch a python script, one to enter presentation mode, one to exit. The scripts are super simple:

```
#!/usr/bin/python

import os

os.system('xrandr --output LVDS --mode 1024x768')
os.system('xrandr --output VGA --mode 1024x768')

```

and...

```
#!/usr/bin/python

import os

os.system('xrandr --output LVDS --mode 1280x800')
os.system('xrandr --output VGA --off')
```

It works like a charm, and is very easy to use...
Hope this helps someone,

-Dave

---

