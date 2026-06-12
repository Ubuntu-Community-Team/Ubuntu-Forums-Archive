---
title: "nvidia-glx-new enabled but not in use"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by richame on 2007-10-19
I realize there are many, many posts about this but I can't find the answer.  Let me try the question from my point of view (or ignorance).

Under Fiesty I had Beryl & Emerald working fine. 

Early on in my Fiesty days I played with loading my own drivers (including the use of Envy) BUT found this to be a pain in that I'm then committed to fixing stuff every time update brings a new kernel.  I was excited to see that Gutsy was including a Restricted driver Manager, but this isn't helping yet.

I have Gutsy up and running but it wants to drop back to failsafe mode.  The restricted nvidia-glx-new driver is installed but never shows as enabled in the Restricted driver Manager.

I'm using a GeForce 7800 GSOC AGP graphics card and am wondering if nvidia-glx-new even works with this.  I've not found any simple lists about which cards to use with nvidia-glx-new, nvidia-glx or legacy.

Running gksudo nvidia-settings inserts 
```

Section "Device"
 #   
    Identifier     "device1"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

```

glxinfo yields
```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 16 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0"
```

Any thoughts?  Sorry if this question (or it's many variants get rather tiring).

Matt

---

### Post by froy02 on 2007-10-20
Use synaptics and check if Nvidia-glx-new is installed. If it is installed but nvidia-glx or nvdia-glx-legacy are installed un-install them.

Note: I think Nvidia-setting or nvidia-xconf  conflicts with the new.  I haven't had time to confirm which one so i recommend not installing them.

---

### Post by richame on 2007-10-20
Synaptic shows nvidia-glx-new is installed. I can uncheck "installed" in the restricted manager and cause the driver to be uninstalled and nvidia-glx iis automatically installed.  This "works" in that I can go back to native screen resolution, unlike failesafe's 600 or 800 x ...

But with nvidia-glx I can't use any eyecandy, if I try to turn on "standard" eyecandy in "apperance" it offers to automatically install nvidia-glx-new.  So, you can see my confusion, the system thinks I can use nvidia-glx-new, but...

So is there a real list?  Assuming this card is on it, I have a config problem.

Thanks,
Matt

---

### Post by jfd on 2007-10-20
I'm having the same problem I think but the card I'm using is a Nvidia Gforce 2 MX-400, and the driver I've installed using Synaptic is called nvidia-glx-legacy.

I know it's the right driver but it doesn't come up on the hardware list so I can't engable it to be able to use it!

---

### Post by mc4man on 2007-10-20
I have the same card and glx-new works fine. As I remember under feisty I couldn't use the "new", but for gutsy I did a fresh install and they were enabled right away. Had to use ```
sudo dpkg-reconfigure xserver-xorg
```  to get  complete resolution choices and then a few tricks to get the proper refresh rates.
If you did an upgrade maybe try above to reconfigure (use advanced when prompted) or fresh install
If you get it enabled and have problems with refresh rates post back

---

### Post by themusicwave on 2007-10-20
I had a similar issue last night I was getting dropped into low hardware mode or low output mode.

This made everything 640X800 or somethign like that.  I was able to fix it an get compiz fusion running perfectly.

First, open synaptic and unistall the following:

antything that starts with nvida-glx also remove the nvidia settings and nvidia config:\
> $sudo apt-get remove nvidia-glx-new nvidia-glx-legacy nvidia-settings nvidia-xconfig



Now reinstall the restricted module for your kernel:
> For the geneic kernel:

sudo apt-get install linux-restricted-modules-2.6.22-14-generic


[QUOTE]For the 386 kernel:

sudo apt-get install linux-restricted-modules-2.6.22-14-386[/QUOTE

Note if you have a duo core you should probably use the generic kernel.  The 386 kernel will only see one of my cores.


OK now open the restricted driver manager by going to

System -> Administration -> Restricted Driver Manage

try enabling the nvidia driver.  At this point the nvidia driver will be reinstalled.  Now reboot and if all goes well you should have compiz fusion and nvidia drivers.

This is all based off my experience at 2am last night, I hope it helps.

---

### Post by jfd on 2007-10-20
Like I said, I can't actuly find it on the hardware listings so I can't do anything like that at the moment lol.

---

### Post by jfd on 2007-10-21
i typed in compiz in the terminal and got this:

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

I've heard about this Xgl but know nothing about it can anyone help?

Sorry to be such a bother lol

---

