---
title: "Dual screen with xrandr problem"
date: 2012-08-12
forum: Multimedia Software
---

### Post by marlin9800 on 2012-08-12
Good morning all, I recently added a second monitor to my 12.04 only to have Ubuntu not see it. I looked it up and decided to use xrandr to get it working. This worked until the first time I rebooted. Now when I startup, I get the login screen in both monitors, the username/password field will move to which ever monitor my mouse is in, I type in my password, screen goes black like it's logining, then right back to the login screen with the drum sound and all. I have booted into recovery mode and attempted to run xrandr from the shell, but no matter what option I use, I get "Can't open display".

Video card is GTX 550ti/ one monitor is dvi, one is vga. Ubuntu 12.04 64bit.

(In the login screen, the two screens look great, resolution is correct, the switching back and forth with the mouse, while annoying, works just fine.)

---

### Post by LiamOS on 2012-08-12
Could you boot up and log in with only one monitor and then plug the second in and then post the output of 
```
$ xrandr -q
```

This seems a really odd problem.

---

### Post by marlin9800 on 2012-08-12
I have tried that, with each monitor, one at a time. It still does the exact same thing.

---

### Post by LiamOS on 2012-08-12
Is xrandr detecting them properly? Is xrandr -q outputting anything weird? Do you know are the appropriate kernel modules loaded?

---

### Post by marlin9800 on 2012-08-12
Any command using xrandr, to include -q, outputs 'Can't open display'. I am not following your second question.

---

### Post by LiamOS on 2012-08-14
I'm not particularly good with monitor detection, but could you post lspci and lsmod? You may have to sudo them if they're not in your path.

---

### Post by happywing on 2012-08-14
1, Enter xrandr into your terminal and figure the name of your laptop screen and the name of your external screen. Mine were VGA-0 for the laptop and LVDS for the external one.

2, While you are on it you can figure the resolutions supported by both devices.

3, Create an executable script somewhere on your computer and name it e.g. dual_monitor.sh.

4, Put the following commands into the script. The comments should explain what is for what!


    #!/bin/bash


    # RESOLUTION SETTINGS
    # This sets your VGA1 monitor to its best resolution.
    xrandr --output VGA-0 --mode 1280x1024 --rate 60
    # This sets your laptop monitor to its best resolution.
    xrandr --output LVDS --mode 1400x1050--rate 60

    # MONITOR ORDER
    # Put the Laptop right, VGA1 monitor left
    # xrandr --output VGA1 --left-of LVDS1
    # Put the Laptop left, VGA1 monitor right
    xrandr --output LVDS --left-of VGA-0

    # PRIMARY MONITOR
    # This sets your laptop monitor as your primary monitor.
    xrandr --output LVDS --primary
    # This sets your VGA monitor as your primary monitor.
    # xrandr --output VGA1 --primary


Just comment out what you don't want and uncomment what you need and you will be done - after running this script!

______________________
[A+ BBB]("http://lepkeautotrans.com")

---

### Post by efflandt on 2012-08-15
I don't think xrandr works properly for non-default video drivers (at least for nvidia).  I know that it throws error "xrandr: Failed to get size of gamma for output default" and does not show proper refresh rate.

If the system does not initially recognize  an added display, it should after either logging out and back into X, or rebooting.

Is there some reason you did not use NVIDIA X Server Settings?  What did you do with xrandr, because usually that is only temporary unless you put something in a script that is running automatically and interfering?

I also have GTX 550 Ti, but with 32" 1080p HDTV have not needed (and do not have room for) more than one display (connected DVI to HDMI).

---

