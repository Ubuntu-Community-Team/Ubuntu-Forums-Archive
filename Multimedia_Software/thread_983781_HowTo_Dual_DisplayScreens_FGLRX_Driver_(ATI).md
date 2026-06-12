---
title: "HowTo: Dual Display/Screens FGLRX Driver (ATI)"
date: 2008-11-16
forum: Multimedia Software
---

### Post by TekNullOG on 2008-11-16
This How-To might be obvious for some but I see a lot of people looking for solutions for dual screens using the fglrx drive from ATI. So I thought I would help.

Let me show you how I've done it for a few years now without any trouble, including 10 minutes ago. It's works since Ubuntu 6.10 for me.

My specs:
ATI X300 mobility
Screen 1: 1400x1050
Screen 2: 1920x1200

Configuring my 2nd screen is always the first thing I do after my fresh install.

Basically, this thread is my reference every time:
[http://ubuntuforums.org/showthread.php?t=301941](http://ubuntuforums.org/showthread.php?t=301941)

I don't follow the commands anymore because I often ran into problems.
[B]
Save a back of the xorg.conf file [/B]
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```
[B]
Open up Xorg.conf using ONE of the following commands:[/B]
Gnome (Ubuntu):
```
gksudo gedit /etc/X11/xorg.conf
```
KDE (Kubuntu):
```
kdesu kate /etc/X11/xorg.conf
```

[B]
Simply copy the following lines to your "Device" Section and edit the appropriate spots:[/B]
```

Option "DesktopSetup"  "horizontal" #Enable Big Desktop
Option "Mode2"         "1280x1024" #Resolution for second monitor
Option "DesktopSetup" "LVDS,AUTO" #the types of monitors that is connected LVDS = LCD, CRT, AUTO
Option "EnablePrivateBackZ" "yes" #Enable 3d support <= May Not Work
Option "HSync2" "65" #This sets the horizontal sync for the secondary display. 
Option "VRefresh2" "60" #This sets the refresh rate of the secondary display.

```

Note: Compiz will not work with the Big Desktop. At least, I've never managed to get it to work.

---

### Post by markbuntu on 2008-11-16
You could also just use the Catalyst Control Center to do that.

---

### Post by TekNullOG on 2008-11-17
Awesome! I was unaware that ATI finally had an interface to configure settings! Wow, I feel like I was left in the dark all this time... haha

It's strange that people don't mention it more often in posts about setting up ATI cards.(well, at least, it is my opinion when reading about people's ati problems) 

It's also unfortunate that when the driver is installed it doesn't add Catalyst to the System > Preferences menu.

BTW, for those that are curious, the command to launch the Catalyst is:
```
amdcccle
```

---

### Post by TekNullOG on 2008-11-18
OK, I am apparently really blind. It is added to the menu but at a very retarded place.

Applications > Accessories > ATI Catalyst Control Center

---

### Post by remmyshroomo on 2008-11-18
Oh boy, well it was all going well with the dual display modes until I got the idea of not having a clone display and make each monitor have its own desktop..

From amdcccle I selected the 2nd Monitor (TV) and change the Multiple display from clone to "Big desktop right of display"

My ATI 200M didn't like that. It flickered everything and then went straight to black screen on both monitors.

Now whenever I boot (or restart x with ctl+atl+bkspc) with the s-video plugged in I get a blank screen. If do not have the 2nd monitor plugged in I am able to get into Ubuntu. Even worse if I am able to pull up the dual monitors forcefully it gives an output of the desktop all scribble.

I have tried restoring the xorg.cfg and reinstalling the drivers and no solution.

Now is there any file that AMDCCCLE writes to with diagnostic information that I might be missing?


Thanks,
Ryan

---

### Post by markbuntu on 2008-11-18
With the second monitor unplugged, boot up and use the Catalyst Control Center to disable the second monitor, reboot  with the second monitor plugged in and then try the autodetect in CCC.

---

