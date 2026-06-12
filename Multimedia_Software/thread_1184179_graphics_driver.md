---
title: "graphics driver"
date: 2009-06-10
forum: Multimedia Software
---

### Post by jimmybond on 2009-06-10
I'm pretty sure some people have had a similar problem as I do, but if anyone could point me to a solution, I'd be grateful. 

I recently installed 8.04 Hardy Heron (still a newb) and used the Update Manager to Upgrade to Intrepid Ibex, and then to Jaunty.  The upgrade to Ibex went smoothly, but the upgrade to Jaunty included some errors, and the kernel could not update properly.  Prior to this, the system installed its own graphics driver 96 automatically from nvidia.  (I have an Nvidia GeForce FX 5200 graphics card.)  

Now, after reboot, with the 173 graphics driver, the X server/file configuration has changed and gave a similar error to this thread:
[http://ubuntuforums.org/showthread.php?t=961869](http://ubuntuforums.org/showthread.php?t=961869)

I've tried a number of methods to uninstall and reinstall the drivers (both 96 and 173), using Ubuntu's Add/Remove menus, as well as some terminal commands, such as:
```
sudo apt-get remove nvidia-glx
```

Somehow I think I messed up the xserver/xorg interfaces during that tinkering, so now I can't log into the desktop properly.  If I do get into the desktop, the shutdown/logoff button at the upper right corner disappears.  (I can add it back but I have to do it each session).  I've tried following some of the suggestions on this thread:
[http://ubuntuforums.org/showthread.php?t=488145](http://ubuntuforums.org/showthread.php?t=488145)
but the ipw2200 network drivers do not load in the recovery terminals.  (I can't reinstall the packages).

Thanks for any suggestions.

---

