---
title: "8800GTS - nvidia driver installation, im stuck"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by final)ark on 2007-07-17
I am fairly new to Linux, but know how to navigate myself through it quite well. Anyways, i have been trying to install my 8800gts drivers on ubuntu 7.04 i386

Specifications:
MSI P6N SLI Motherboard
2gb Gskill ram
160gb WD hard drive
evga 8800GTS 320mb video card
Intel e6600's 
lotsa thermaltake power :P


I have tried:
-Using Envy, as suggested in my last post ( [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) )
-Using a suggested guide ( [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty) )
-Using NVIDIA's How to from nvidia.com

All the solutions lead to the same exact problem. I can install the driver fine, and it tells me to reboot. So I reboot, and then come to a blue/grey/red weird lookin xorg screen that tells me xorg is messed up and i need to configure it and then restart the GDM. So i usually just go through xorg (sudo dpkg-reconfigure xserver-xorg) not changing anything and just hitting "ok" on every page, and then my system loads, but at this point my driver says its still not installed. 

Any ideas? Again im fairly new to this all, im hoping this is an easy fix :P

---

### Post by dabl on 2007-07-18
Bummer!

This is probably a long shot -- but here's what I would try.

First, I'll assume you have downloaded Envy AFTER June 22, because that is when he put the 100.14.11 driver version in that your 8800GTS requires.  So, I would boot Ubuntu in Recovery Mode (no GUI), log in at the text prompt, and run Envy in text mode, with ```
sudo envy -t
```and let it install the driver.  When it says "do I want it to start the X server" I'd say "YES" and pray.

If it's still no good, I would Ctrl-Alt-F1 to a text login, login, and run ```
sudo nvidia-xconfig --add-argb-glx-visuals --composite
```and see if that fixes it.

You might also review your BIOS settings and make sure there's nothing that could conceivably interfere with the display, like some "power management" or "sleep behavior" stuff.

I sure hope you get it working!  :)

---

### Post by final)ark on 2007-07-18
That did not work, but sort of pointed me int he right direction. I somehow ran into this post:

[http://ubuntuforums.org/showthread.php?t=497284&highlight=the+right+way](http://ubuntuforums.org/showthread.php?t=497284&highlight=the+right+way)

And i did it step by step.. To find when i restarted, my nvidia drivers were fully functioning, beryl installed with no issues, all the resolution settings were avaible, everything... So if you have a 8800GTS and are having trouble installing your drivers, use the link up there ^^^

That really deserves a sticky, because none of the freaking stickies work, but this one actually does. Screw the people trying to write gay scripts and all this **** that doesn't even work. Follow the right guide: 

[http://ubuntuforums.org/showthread.php?t=497284&highlight=the+right+way](http://ubuntuforums.org/showthread.php?t=497284&highlight=the+right+way)

Problemo solved

thanks for the help

---

### Post by dabl on 2007-07-18
Excellent!  Yes, that is a very well-written instruction -- I just reviewed it.  :popcorn:

---

