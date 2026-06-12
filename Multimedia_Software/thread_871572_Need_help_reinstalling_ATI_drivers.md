---
title: "Need help reinstalling ATI drivers"
date: 2008-07-27
forum: Multimedia Software
---

### Post by casperiv on 2008-07-27
So to start, this is a Hardy machine with an ATI 2900.

I went to the ATI site and downloaded the latest drivers in hopes of improving frame rates in some games I was playing, one being World of Warcraft.  Anyway, after installing them, the game is unusable (it's extremely fragmented/lots of artifacts).  So, I wanted to uninstall the drivers and reinstall the older ones.  First problem is that it tells me I can't uninstall them due to dependency issues... yet doesn't tell me what depends on them.  Second, I can't install over the top, because I don't really know what version of driver was on the install disk to begin with, and that version was working.

Any help?  I just want to get this thing back in working order.


PS: The strangest part of my current problem is that while the games look totally distorted on my monitor, they actually look ok when I take a print screen, and yes, the monitor can handle the rez.  It's strange.

---

### Post by markbuntu on 2008-07-27
How did you install the driver? 

Which directions did you use? 

The only ones I know of that work for sure are here:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

You can also try fooling around in the Catalyst Control Center to adjust the anti-aliasing etc. You can also try some of the adjustments reccomended here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)


But the easiest thing to try first is to turn off the desktop visual effects before stating wow. If that does not work, try the adjustments.

---

### Post by casperiv on 2008-07-27
I installed them following the directions there on the wiki.  I also uninstalled them (after fighting with it again today) and reinstalled them, only to have an even bigger problem.

There were no visual effects turned on my desktop, and the drivers were the most current from ATI's site.

In the end I just nuked it and am reinstalling from scratch.  I guess this is a chance to get even more practice installing from ground zero.  After the reinstall, I have problems even on my desktop, where as before I only had OGL issues.

---

### Post by markbuntu on 2008-07-27
If you are reinstalling from scratch, the first thing you should do is install the ATI driver with the directions from the link above, method 2. It is vitally important to follow the directions very carefully. 

If you cannot enable the desktop effects, then you do not have the driver correctly installed, try again, and don't forget to reboot or the correct kernel modules will not get loaded.

---

