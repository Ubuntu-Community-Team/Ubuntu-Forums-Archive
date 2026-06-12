---
title: "Dell 2407WFP stuck at 50hz"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by fasolatha on 2007-04-20
Hey all I have a Dell 2407WFP running on a Geforce 6600.  On the initial install the monitor was set to 1024x768@60.  So I changed the xorg.conf and enabled the nvidia driver from the restricted hardware list to make it run at 1920x1200@60 which is its native resolution.  It now works at 1920x1200 but the only option in refresh rate list is 50hz?!  Works perfectly fine in Windows at 1920x1200@60hz

Any ideas?

---

### Post by linuxguy on 2007-06-06
I have that same problem and it frustrates the hell out of me, especially since it was working fine until today. I have the same monitor, and an NVIDIA GeForce 7600 GS, with a DVI connection. I can only get 1920x1200 @ 60Hz with the free nv driver, but its performance is sub-par. If I use the newest proprietary driver, that same resolution peaks at 50 Hz, since this morning.

Update -- Apparently there's an issue with the proprietary driver which causes incorrect display of the actual refresh rate. To fix this, add the following to the Device section of your xorg.conf file:  
```
Option    "DynamicTwinView"    "false"
```

---

### Post by fasolatha on 2007-06-17
Thanks for the reply linuxguy.

After searching for days online for a fix and not finding one I was told by a friend that the current screen res is displayed in the monitors preferences, I originally thought that the display options there was info on what the monitors default screen resolution is not the actuall output.  It currently shows 1920x1600@60hz but the screen resolution tool under preferences still shows 50hz.

In my attempt to find out what was wrong with the setup I came accross the nvidia driver install tool called envy, I installed the latest nvidia drivers and also found out that the drivers come with a command line called "nvidia-settings" which allow you to set up resolution etc.  On the settings tool it also showed 60hz.  

So I came to the conclusion that nothing is actually wrong with the setup, just an issue with the Screen Resolution tool in the Preferences menu.  *sigh* :roll:

Thanks again.

---

