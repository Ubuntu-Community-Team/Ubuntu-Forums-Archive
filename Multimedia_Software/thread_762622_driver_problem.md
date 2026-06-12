---
title: "driver problem"
date: 2008-04-22
forum: Multimedia Software
---

### Post by Enthrall on 2008-04-22
So im pretty new to linux. Im really stuck right now. I have the geforce 9600 gt so i tried to install the new nvidia driver they have out for it. It all goes well untill I decide to save the settings and restart. They dont actually save and it just goes back to 800 x 600. I logged in with root and tried to save it let me but again back to 800 x 600 on restart. Usually logging in with the user it tells me that it cant delete the temporary file xorg. Please help me out guys I've been looking for about 3 hours now. And Im trying to get away from my vista os.

---

### Post by Enthrall on 2008-04-22
OMG can someone help me it just keeps loading up into low resolution. Instead of my nvidia driver!!??

---

### Post by SynthesizersFTW on 2008-04-29
I used EnvyNG for the driver install of my 8800GT, and afterwards the same thing happened, resolution falls back to failsafe 800x600.

All your resolution settings are in your [FONT="Courier New"]etc/X11/xorg.conf[/FONT], you have to manually enter the settings supported by your display, or you can use

[FONT="Courier New"]sudo dpkg-reconfigure xserver-xorg[/FONT]

In particular, you will want to look for the lines:
SubSection     "Display"
        Depth       24
        Modes      "1280x1024@60" "1024x768@60"

The Modes are what you're after.  
Also, the nvidia tools themselves have a variety of options, if you haven't already done so, install the "nvidia-settings" package with Synaptic.

Good luck!

---

### Post by Azraelthe7th on 2008-04-30
Envy won't help, as the full drivers for the 9600 GT haven't been released on Linux.  You could try compiling them yourself or wait until the drivers see a complete release. In the meantime, try using the Vesa or nv drivers, as they'll allow you to use your PC, but with no 3D support, for now.

---

