---
title: "Dual Display - Set Primary Monitor"
date: 2008-12-01
forum: Multimedia Software
---

### Post by grimace84 on 2008-12-01
Just installed 8.10, I have a dual display setup and it's all working fine, I have the desktop extended across the two monitors.

At the moment the primary display is the laptop monitor, but what I want, is the for the external display to be the primary one - there is no way to configure this in the GUI.

I gather I need to manually edit the xorg.conf file, but this has changed since earlier versions and I'm not sure what needs to go in there...

---

### Post by moordbij on 2009-03-05
Hi grimace,

By default, X looks at the CRT monitors first (i.e. your VGA output, doesn't have to be a CRT), then it looks at DFP (digital flat panel) monitors (on your DVI output), and finally it looks at TV outputs. If you're using nVidia graphics card and drivers, this can be circumvented using TwinView.

1. Backup your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
2. Open your xorg.conf file with gedit (or any other text editor of your choice):
```
sudo gedit /etc/X11/xorg.conf
```
3. Add the following lines to the "Screen" section:
```

    Option "TwinView"                               # enables TwinView
    Option "TwinViewXineramaInfoOrder" "DFP, CRT"   # this tells which output should be the primary screen for X
    Option "MetaModes" "1680x1050 1280x1024"        # change the resolutions here to fit your displays
    Option "TwinViewOrientation" "DFP LeftOf CRT"   # how your second screen is placed in relation to the first one
                                                    # LeftOf can be LeftOf, RightOf, Above, Below, and Clone

```
4. Restart X by pressing <control><alt><backspace> and enjoy!


Hope this helps!

Regards

---

### Post by johnmay on 2010-11-29
Here is another solution: 

[http://ubuntuforums.org/showthread.php?t=1309247](http://ubuntuforums.org/showthread.php?t=1309247)

---

### Post by kgenus on 2011-06-05
**SITUATION**
After upgrading to Ubuntu 11.04 Natty Narwal in my recording studio, I had a problem, or as I would rather put it, a challenge.  The challenge was as noted earlier, X11 sets the display connected to the CRT port as the default display.  In my case, the displays are driven by an NVidia GT240, and the monitor on the CRT port is located down the hall inside a vocal booth, while the other monitor sits at the recording console.  Simply put, the login screen was showing up, but you had to walk down the hall to see it.

**SOLUTION**
Edited /etc/X11/xorg.conf added the option "UseDisplayDevice" "DFP" to  first screen section.  Please see the Bold/Blue text below.  After rebooting the initial display came up as the same resolution as the CRT monitor, I adjusted that to 1920x1200 and that was pretty much it.

Section "Screen"[INDENT]Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
[COLOR=Blue]**    Option         "UseDisplayDevice" "DFP"**[/COLOR]
Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1920x1200 +0+0"
    SubSection     "Display"[INDENT]         Depth       24
[/INDENT]EndSubSection
[/INDENT]EndSection


Hope this helps.

---

### Post by mossontherock on 2011-07-24
Here's what worked for me:
Given that I'm using a laptop and my laptop screen identified as LVDS1 and the external monitor as VGA1, I set up three icons that run a script, to switch between clone, dual with LVDS1 as primary, and dual with VGA1 as primary.

Using the text editor Kate I created three files with the names:
VGA1-Primary.sh
LVDS1-Primary.sh
Clone-Monitors.sh

The text contents of VGA1-Primary.sh are:
xrandr --output VGA1 --right-of LVDS1
xrandr --output VGA1 --primary


The text contents of LVDS1-Primary.sh are:
xrandr --output LVDS1 --left-of VGA1
xrandr --output LVDS1 --primary


The text contents of  Clone-Monitors.sh are:
xrandr --output LVDS1 --auto --output VGA1 --auto --same-as LVDS1


For each file I enabled in properties permission or chmod to execute.  The result is an icon that you can click to switch between dual monitor, clone and switch the primary display, without using KrandrTray (Screen resize and rotate) which sometimes crashed my display screen when switching modes.

---

