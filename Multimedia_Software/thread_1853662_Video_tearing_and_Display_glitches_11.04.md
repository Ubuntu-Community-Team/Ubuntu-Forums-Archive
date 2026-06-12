---
title: "Video tearing and Display glitches 11.04"
date: 2011-10-02
forum: Multimedia Software
---

### Post by BatteryKing on 2011-10-02
OK, I finally figured out how to get the window manager to work in 11.04 after nearly a half year of absolute frustration and so I thought I should share.

Basically the problem is all of the Unity and Compiz-Fusion changes (specifically Composite) put into 11.04 is a big, steaming pile of doo-doo and even some of the historical methods of disabling the broken stuff are also broken, so there are a few extra tricks involved.  However once you finally get it all disabled for real, suddenly you will be able to see what is on your screen, no wall paper showing through and no tearing of your videos.

Here is what to do:
1. Disable Unity - At the bottom of the login screen is a drop down where you can select the "classic" window manager.  Do this and you will immediately be much happier.
2. Fully disable Compiz-Fusion Composite - Historically Compiz-Fusion has been less than perfect, but in 11.04 it is so broken that even the normal mechanism to disable the brokenness is broken.  But don't fret, there is a way around this.  Here are the two main steps involved:
      a. Install compizconfig-settings-manager.  In the settings manager, go to general and uncheck Composite.  This will ask you if you want to disable a bunch of different things.  Say yes.  Don't think about it just do it as all of the things mentioned here pertain to the cookie jars compiz-fusion is getting its fingers into and messing up.  However this is not the end of it as the Compiz Composite stuff will still start up.
     b. Disable Composite on X11 startup.  I found this little nugget here ([http://forum.xbmc.org/archive/index.php/t-100898.html](http://forum.xbmc.org/archive/index.php/t-100898.html)) and this is when my desktop finally started to work right.  Type in the command `sudo nvidia-xconfig --no-composite`.

Reboot for good measure and enjoy!

---

### Post by mikewhatever on 2011-10-02
Over dramatic, and way too complicated. Why not use metacity instead of compiz?

---

### Post by BatteryKing on 2011-10-02
Several of my friends have switched back to Windows 7 in recent months and I guess their mentality of Ubuntu as of late has been rubbing off on me a little.

---

