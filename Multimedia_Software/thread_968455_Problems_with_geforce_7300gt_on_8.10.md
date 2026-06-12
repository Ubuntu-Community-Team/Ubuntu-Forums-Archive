---
title: "Problems with geforce 7300gt on 8.10"
date: 2008-11-02
forum: Multimedia Software
---

### Post by boddhisatva on 2008-11-02
I have a GeForce 7300GT video card and it ran (nearly) perfectly on 8.04 on an Envy-installed driver. I'm on Pentium4, display is 1650x1050. After upgrading to 8.10 the drivers don't work - neither the EnvyNG-recommended (173 series) nor the one recommended by the proprietary driver utility in Ubuntu (177 series). The release notes said there could be problems but only with older processors (below Pentium3). I'm at a loss. Is it possible to downgrade to 8.04?

---

### Post by Dittie on 2008-11-02
Check out this link and see if the solutions others have found will work for you :) Good luck!

[http://ubuntuforums.org/showthread.php?t=965180](http://ubuntuforums.org/showthread.php?t=965180)

---

### Post by boddhisatva on 2008-11-03
Thanks for the link. Unfortunately, none of the suggestions have worked for me. Now after compromising the kernel with the (non-functional) driver from NVidia site, I can't even re-install the (non-functional) drivers via Synaptic/proprietary driver utility, as an error occurs (it sees "/usr/lib/xorg/modules/extensions/libglx.so" in xserver-xorg-core, so it won't overwrite it - I guess the nvidia installer has changed it. Not that I know much about it...).
I still hope it's possible to downgrade to 8.04. In worst case scenario I'll reinstall 8.04. Well, silly me, I should have waited a couple of weeks until they've made a fully-functional distro. And I was going to, but suddenly I wanted to run the Gimp 2.6.2 .deb, which was for 8.10 only... 
For the time being, I'm back to a distorted lower-res display with no 3D. (I've got widescreen 1600x1050, and it's running at 1280x1024)

---

### Post by boddhisatva on 2008-11-03
Well, I've re-installed some modules in Synaptic and the situation is "back to normal". The drivers aren't working, but at least the system is back to "factory state". I'll try the generic nv for the time being (maybe it will handle the resolution). Bye 3D, bye desktop effects! At least, until an 8.04 re-install or a miracle from Canonical ;)

---

### Post by boddhisatva on 2008-11-03
After changing "nvidia" to "nv" in xconf the display is OK. The only problem is I forgot my main tool is Blender and I won't go far without 3D... So it's probably 8.04 reinstall for me...
Next time I'll make sure to make a system backup...

---

### Post by boddhisatva on 2008-11-03
I meant xorg.conf :)

---

