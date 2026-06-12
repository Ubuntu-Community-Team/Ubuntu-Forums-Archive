---
title: "DRI driver missing for trident"
date: 2011-03-22
forum: Multimedia Software
---

### Post by ChristBornPaladin on 2011-03-22
First things first: Toshiba Portege 3500, Ubuntu Netbook 10.10

I've had the same fight with the Trident CyberBlade Ai1 that everyone else who puts Linux on one of these does.

I created /etc/X11/xorg.conf to use the X11 2D driver, fix the resolution, and actually stretch the image across the screen when the resolution is less than 1024x768.

Through various forum searching and a few terminal commands I don't remember, I've got the following hiccups.```
glxinfo | grep direct rendering
```yields```
direct rendering: yes
```



However:```
xdriinfo
```yields```
Screen 0: not direct rendering capable.
```



```
cat /var/log/Xorg.0.log | grep AIGLX
```yields```
[    32.429] (==) AIGLX enabled
[    32.805] (II) AIGLX: Screen 0 is not DRI2 capable
[    32.805] (II) AIGLX: Screen 0 is not DRI capable
[    32.977] (II) AIGLX: Loaded and initialized /usr/lib/dri/swrast_dri.so
```




I checked and the **trident_drv.so** exists for X11, and **swrast_dri.so** exists for Mesa. I pulled **trident_dri.so** from an old version of Mesa and dropped it into **/var/lib/dri/**, but Mesa isn't looking for it. I pulled **trident_dri.so** drivers from a Fedora rpm for X11 and dropped them into the **/var/lib/xorg/modules/drivers/**, but once again, it won't load them, and I don't know how to manually load that module in the xorg.conf file, or if that's even possible.

After version 7.5.2, Mesa apparently dropped 3D acceleration support for all trident graphics cards. I was going to try my hand at compiling that version of Mesa into place, but I'm apparently missing something, because all I get is error after error, and the compile doesn't complete successfully. I've loaded all the pre-reqs I can find, and it still won't successfully compile.

What I want is working 3D acceleration and OpenGL. It existed at one point in the past, but now it doesn't, and most people who install Linux on this graphics card post adulation in the forums when their screen resolution kicks up to display native, so I'm kind of up a creek here.



xorg.conf and Xorg.0.log files attached in zip.

Draw speed is a mite slow in some instances, and obviously 3D games do not work. Trying to turn screen effects on yields "Screen effects cannot be enabled."

EDIT: I also can't log into Unity.

---

### Post by ChristBornPaladin on 2011-07-08
Ubuntu 11.04 update.

Unity works if X11 isn't able to load the window manager I choose for whatever reason. It just jumps down to Unity, which barely works and very slowly. Curious problem has popped up.  Anacron is starting and stopping over and over. I can open a login prompt with ctrl+alt+F2, log in and start X or LXDM/GDM, but the anacron process is stuck starting and stopping forever. Trident
video issues identical to previous version of Ubuntu.

Will update later today with a screenshot.

---

### Post by ChristBornPaladin on 2011-07-08
Screenshot of the new errors.  No idea if they're relevant or not.

---

