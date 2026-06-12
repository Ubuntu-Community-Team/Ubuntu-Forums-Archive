---
title: "Nvidia 8800 GTS driver probs"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by BrownieBoy on 2007-09-04
Just treated myself to a shiny new Nvidia 8800 GTS, and what a stormer it is!  After several tries, I seem to have got Nvidia's proprietary driver installed, but whenever I reboot Ubuntu, the X Server fails to even load.

To get it load in that case, I have to

*sudo nano /etc/X11/xorg.conf*

and change the Section "Device" Driver entry from "nvidia" to "nv" and then reboot to get X to load up.  Once in X, I issue a

*sudo nvidia-xconfig*

followed by *Ctrl->Alt->Backspace *to restart X, and voila!  I have a fully working 3D Nvidia driver, with a gorgeous 60fps in Doom 3.  But as soon as I do a full reboot of Ubuntu again, I'm back to X server refusing to start, which in order to cure I have to change the "nvidia" entry in xorg.conf to say "nv" ... which is where we came in.

It seems like some settings somewhere are getting reset every time I reboot Ubuntu.  Here's hoping one of you kind people out there can point me in the right direction.

I hate Windoze with every fiber of my being, but I have to say that installing the equivalent driver on Satan's platform took under 5 minutes, whereas I've been searching through the forums for the best part of 4 hours trying to nail my Ubuntu issues.

Cheers,

Brownie

---

### Post by tseliot on 2007-09-05
There is a bug in the driver in Ubuntu's repositories which affects geforce 8xxx cards.

You can:
1) install the driver from Nvidia's website by following method 2 of my guide:
[http://ubuntuforums.org/showthread.php?p=2587126](http://ubuntuforums.org/showthread.php?p=2587126)

2) try Envy (at your risk) and solve the problem in few clicks:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Please follow either one method or the other. Don't mix them.

---

### Post by IanW on 2007-09-05
I also bought an 8800GTS this week, and Tseliot's Envy script worked perfectly for me.
Allthough I had to boot to "Recovery mode", and run it in text mode using "envy -t".

---

### Post by davedumas0 on 2007-09-13
i HAD the same problem  envy was not working until i downgraded my envy to 9.5 (was 9.7)
and that fixed my problem it even built a nvidia kernal
i have a geforce 8800 gts oc

---

### Post by Clarko on 2007-10-22
I have the EXACT same problem since 7.10.  I had no problems in 7.04, but ever since I upgraded (fresh install, too) I can't boot up without going into low-graphics mode.  I can reinstall the driver and it works perfectly until I restart.

This is a very frustrating bug :(

---

### Post by blakeg on 2007-10-22
I know there's a nice howto somewhere here on the forums for installing the Nvidia drivers manually. requires downloading them and running several command lines, but it has always worked for me. I seem to remember uninstalling all the "restricted" related packages on my install.

The guide was for 7.04, but also worked seemlessly with 7.10.

BTW, I also have a BFGTech 8800GTSoc.

let me find that link, maybe that will fix your issues.

EDIT: here is the link. [http://ubuntuforums.org/showthread.php?t=497284&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=497284&highlight=nvidia)

---

### Post by Chbuntu on 2008-02-18
> **tseliot said:**
> There is a bug in the driver in Ubuntu's repositories which affects geforce 8xxx cards.

You can:
1) install the driver from Nvidia's website by following method 2 of my guide:
[http://ubuntuforums.org/showthread.php?p=2587126](http://ubuntuforums.org/showthread.php?p=2587126)

2) try Envy (at your risk) and solve the problem in few clicks:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Please follow either one method or the other. Don't mix them.

Is it possible Envy installs the wrong driver? because in the envy menu it just says "install Nvidia driver" not really specifying which driver for which model. Ive gotten my drivers working adequately with envy, besides the fact that in windows (I'm dual booting with vista) the Nvidia control panel is waaaay better with more resolution options and whatnot. Ive ve got only one problem left with my twinview, my hdtv's resolution is a little too big (borders missing). btw ive only been on ubuntu for a week or so.
heres my specs:

Ubuntu 7.10 gutsy gibbon
Nvidia geforce 8800gts
samsung syncmaster 920nw native resoloution: 1440x900
Sharp LC 32sh20u HDTV native resoloution: 1336x768

also, maybe someone has some suggestions for a good setup with my tv :D

---

### Post by pondochris on 2008-03-10
> **Chbuntu said:**
> Is it possible Envy installs the wrong driver? because in the envy menu it just says "install Nvidia driver" not really specifying which driver for which model. Ive gotten my drivers working adequately with envy, besides the fact that in windows (I'm dual booting with vista) the Nvidia control panel is waaaay better with more resolution options and whatnot. Ive ve got only one problem left with my twinview, my hdtv's resolution is a little too big (borders missing). btw ive only been on ubuntu for a week or so.


I'm actually on my third envy/nvidia update.....if you go to Nvidia.com and see they have a new driver version and wish to update it, get the newest envy and follow the directions on the envy site to remove the previous driver and version of envy.  you must then install the new version  as directed, then run it to install the driver(the current update I had to log out and then drop to a terminal, run "sudo envy -t" after installing envy.  (would be incredibly awesome if envy got so good that: it could search for, and install the new version with a click.)

The Nvidia-Settings is featured enough for me, however you are right about the control panel in windows being better....I believe this is due to the Nvidia business model.  If I'm not mistaken, Nvidia has to shell out big $$$ for rights and access to code from microsoft so.....they spend the most time and effort developing their drivers and toolkits for windows.  Microsoft is where the money is and that is where the majority is........it's really just icing on the cake for them to produce good linux drivers, and possibly the reason that the linux drivers are about 10 versions behind the windows ones.  

I am very grateful to Nvidia for producing good cards, drivers, linux drivers, and grateful for the guy (Albert Milone?) who developed envy(I could not get the driver from Nvidia to work correctly until I installed envy).:KS

---

### Post by d.j.schroeder on 2008-03-12
Just a short testimonial:  Envy worked perfectly to get the driver for my 8800 GTS in 7.10.

---

### Post by Chbuntu on 2008-03-13
still with the newest nvidia drivers (169.12)  i'm still dealing with overscan or maybe underscan, i'm not sure. either way the newer drivers show no sign of change in the nvidia settings menu. so that leaves me with one last option witch I haven't tried, going into my xorg.conf and editing the modelines.

heres what im sitting on:

Ubuntu 7.10 gutsy gibbon
Nvidia 8800gts.
19" Samsung syncmaster 920nw. native resolution: 1440x900
32" Sharp LC 32sh20u HDTV. native resolution: 1336x768
DVI to HDMI cable if that matters.
compiz

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:21:33 PST 2008

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 100.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTS]"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 GTS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0, DFP: nvidia-auto-select +1440+0"
EndSection


```

Any modeline edit suggestions to acheive a 1336X768 resoloution on my secondary monitor would be appreciated:)

---

### Post by pondochris on 2008-03-14
I would try thi while both are enabled and working:

Go to terminal and run this:

Sudo dpkg-reconfigure xserver-xorg

This may let you configure the resolution manually. If not let me know and I'll do dome more research this weekend as I'm having a similar issue using my hdtv as a second monitor...I'm not even getting widescreen options in nvidia-settings.

Let me know if it works please.

---

### Post by Chbuntu on 2008-03-17
erik@erik-desktop:~$ Sudo dpkg-reconfigure xserver-xorg
bash: Sudo: command not found
erik@erik-desktop:~$ 
 
I've done a xorg reconfigure before but I cant remember the command I used. Anyhow that didn't help either.

---

