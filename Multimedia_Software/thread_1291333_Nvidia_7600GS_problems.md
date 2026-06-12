---
title: "Nvidia 7600GS problems"
date: 2009-10-14
forum: Multimedia Software
---

### Post by futhamucka on 2009-10-14
I just installed 9.04 on my computer. I have been unable to get the screen to display anything greater than 800x600. I tried installing the nvidia drivers using the hardware driver utility. I restarted, and now it's stuck at a maximum of 640x480!
I'm using a 19" HDTV connected with a VGA cable, it has a 1440x900 native resolution.
I'm a returning to linux after years (I used it in college 10 years ago) so I don't really know where to start troubleshooting. Can anyone help? Please let me know what I need to post to aid the diagnosis.

---

### Post by hellblazer on 2009-10-15
NVidia supplies a settings program to change resolution etc.
Click on System > Administration > NVIDIA X Server Settings

If you do not have this option you will need to install it.
```
$ sudo apt-get install nvidia-settings
```

Also, this will only be available if you've successfully enabled the NVidia drivers. To check this go to System > Administration > Hardware Drivers. One of the options should have a green light next to it and when selected it should say *This driver is activated and currently in use.* at the bottom of the screen.

---

### Post by futhamucka on 2009-10-15
I actually have the nvidia-settings installed and running, when I use it to try to change the resolution I am presented with the choice between 640x480 and 320x240! I couldn't get any other choices to appear.

---

### Post by hellblazer on 2009-10-15
ouch! another thing we can try is to have a look at your xorg.conf file, it's under /etc/X11

It has all the settings for your monitor, graphics card, keyboard and mouse

There's a chance that it got garbled somehow and now your stuck with the small resolutions

---

### Post by futhamucka on 2009-10-15
> **hellblazer said:**
> There's a chance that it got garbled somehow and now your stuck with the small resolutions

This is entirely possible, I've been messing around with different suggestions that I have found on this forum. I'll post it when I get home tonight.

---

### Post by futhamucka on 2009-10-15
I restored the oldest xorg.conf backup I could find, it looked like this:
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

```

Then I re-installed the nvidia driver using the package manager, rebooted and it enabled me to get to a maximum of 1360x768! Pretty close!

The xorg.conf now looks like this:
```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
EndSection

```

I can tell I'm almost there. How can I get it to go to 1440x900?

---

### Post by FoxxConn on 2009-10-15
I'm having  precisely the same problem with my Nvidia card.

i found my xorg.conf and all the values were exactly the same as your first set.  I'm only on my second day of the "Linux experience" so if you could help me out with the steps you went through to get a higher resolution i'd be  eternally  grateful  for getting me out of my 640x480 hell.

---

### Post by FoxxConn on 2009-10-16
after uninstalling, reinstalling, and updating the Nvidia driver my Xorg.conf matches all the values of your second set (the set that got you up to 1360x760) except for one extra line under the 'Section "Screen".'
 
 ```
Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Option    "AddARGBGLXVisuals"    "True"
    DefaultDepth    24
EndSection
```could that "Option" line be the source of all my trouble?

---

### Post by hellblazer on 2009-10-16
I found [another thread]("http://ubuntuforums.org/showthread.php?t=444960") that seems to solve this problem.

Hope this helps :P

---

### Post by futhamucka on 2009-10-16
I tried adding the line
```
Option "ModeValidation" "AllowNon60HzDFPModes, NoVertRefreshCheck, NoEdidMaxPClkCheck, NoHorizSyncCheck"
```to the xorg.conf like it said in that other post. When I restarted I got an 'Unsupported Mode' warning from my monitor.
I think I might have to configure the screen driver too, how do I get that set up?

---

### Post by hellblazer on 2009-10-27
I'm sorry, but I've run out of advise :(

Maybe try searching google for your problem, it could've been solved on another forum

---

