---
title: "Having issues getting Xinerama working"
date: 2011-11-07
forum: Multimedia Software
---

### Post by ddkreiser on 2011-11-07
I have a new PC with a FirePro V4800 video card to which I have added an old Radeon HD4550 in order to get a three-headed big desktop.  On startup, I can let xrandr default the configuration to two displays on the V4800, but when I created an xorg.conf file to add in the third monitor on the 4550, all I have gotten is three mirrored images instead of the single big desktop.  I have Xinerama set to true and have seen the message in the /var/log/Xorg.0.log file which stated that Xinerama was enabled, and I didn't see any errors in the log file.  It just seems as if it just doesn't want to extend the desktop across all three monitors, although I will admit that this is the first time that I have tried to modify the xorg.conf file by hand, so I may have messed something up.

Does anyone see what I have done incorrectly in the attached xorg.conf file?  Thanks for any help you can give.

---

### Post by almursi on 2011-11-07
Hi, if you run "aticonfig --help": 
 
"Multi head  :    aticonfig --initial --heads=4 --adapter=1 
This command will generate 4 adjacent X Screens 
on adapter 1.  Use with -f to reduce previously 
configured heads."

Change to --heads=3 and try it, after it's more easy fix by hand. Regards.

---

### Post by ddkreiser on 2011-11-07
I guess I should have mentioned that I am not using the ATI proprietary driver, but I'm using the default radeon driver.  I didn't have much luck with the fglrx driver, so I switched back to the supplied drivers.  Without their driver installed, I don't have aticonfig.

---

### Post by almursi on 2011-11-07
Sorry :) I seemed to see an error with definition of the dependency tree, between monitor, display and device, thereby generating an automatic setting then you could try to adapt more easily. 

If you can not, maybe in the screen section, subsection display, you can adjust a diferent "viewport" (among a global "virtual") for every device/screen. Regards.

---

### Post by ddkreiser on 2011-11-07
I changed a few things and tried again - to no avail.  I looked through the Xorg.0.log file and did find this error:

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

??? Why is it trying to load nvidia when I am using the radeon driver?

---

### Post by almursi on 2011-11-08
Hi, perhaps because it is the same for both. On the other hand I have turned to look and I can suggest these changes:

In each "Monitor" add this line (i.e. adjust position for each: 0 0, 1280 0, 2560 0 ):
Option	    "Position" "0 0"

In each "Screen" subsection "display" (i.e., sum total of the three monitors):
Virtual   3840 1024
(if it does not work yet, add to this the viewport with the same position as in the monitor section, i.e. : Viewport 1280 0)
Regards.

---

### Post by ddkreiser on 2011-11-08
Well, thanks for trying, but all you have done is created a big virtual screen for each monitor.  I guess I am out of luck. :(

---

### Post by almursi on 2011-11-08
Hi, well, modify it by hand is usually complicated. With gnome-display-properties (actually xrandr front-end), I have generally achieved better results, but I've never tested with two cards so I do not know what will be capable of displaying. However you can always try to fix it via xrandr command. With "xrandr -q" you see about screens connected and, maybe, you can find the commands required to configure it properly (surely you should ignore my suggestions about Virtual). Some include the command in the startup, if it is easier that configure xorg.conf :). Regards.

---

### Post by almursi on 2011-11-09
> **ddkreiser said:**
>  (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

Hi, maybe fix with:
"sudo apt-get install libgl1-mesa-dri libgl1-mesa-glx"
and "sudo apt-get install mesa-utils" for test with glxgears.

Regards.

---

