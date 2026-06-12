---
title: "Scale display to fit a TV that forces overscan?"
date: 2014-07-12
forum: Multimedia Software
---

### Post by mastakebob on 2014-07-12
My Ubuntu HTPC is getting the edges of its desktop chopped off when displayed on my TV screen.  My TV is low end and I can't turn off 'overscan'.  How can I scale my video output from the Ubuntu side?  Preferably using a graphical utility so I don't have to muck about with trial & error-ing my display config files?

I have XBMC installed on Ubuntu 14.04 hooked up to a 32" Panasonic display.  I have been unable to find a way to disable the 'overscan' function on the TV.  XBMC comes with a built in utility to scale the video output to match the TV screen (a click & drag bracket at each corner of the display allowing me to graphically fine tune the scaling factor).  Unfortunately, this fine tuning doesn't carry over to when I'm in the base Ubuntu desktop.  As such, I'm missing most of my Unity launcher and all of my upper task bar, making it very difficult to navigate my base desktop.  

Most of the internet advice tells me to simply turn off overscan on my TV.  Unfortunately, my TV doesn't have that option.  The few internet answers that deal with adjusting Ubuntu are all from pre-2010 and are not very helpful.  And they  all seem to deal with fiddling with your xorg.conf file on a trial-error basis which I'd rather not do.  

Does there exist a graphical utility that will allow me to click & drag the corners of the screen to 'counteract' my TV's overscan settings and then write those adjustments to whatever file they need to be written to?  

Edit:  I'm using all default, out-of-the-box drivers.  I have a GeForce 8400 GS video card.  

Thanks!  

-Kevin

---

### Post by tgalati4 on 2014-07-12
Open a terminal:

```
man xrandr
xrandr -q
```

There are pan and scale switches that you can use to move the display around.  Take notes and make small changes.

---

### Post by mastakebob on 2014-07-12
Thanks!  

For others who may have this problem:  I fixed this by installing the proprietary nvidia drivers (additional drivers->select one of the proprietary Nvidia binary drivers).  In the nvidia x server settings app (comes when you install the proprietary nvidia drivers), there's an 'underscan' slider bar that allows you 'zoom out' of your desktop, counteracting the TV's overscan.  Fiddle with it until you get the display lined up with your monitor.  Note that nvidia x server settings don't, by default, persist after reboots (meaning everytime you reboot you lose all of your tweaks).  To make your display and underscan settings persist, you have to edit one of your startup scripts (I chose my /etc/X11/xinit/xinitrc) and add  "nvidia-settings --load-config-only" somewhere in it.  See [ftp://download.nvidia.com/XFree86/Linux-x86_64/1.0-6106/nvidia-settings-user-guide.txt](ftp://download.nvidia.com/XFree86/Linux-x86_64/1.0-6106/nvidia-settings-user-guide.txt) section 4 for exact details.

---

