---
title: "Can't Detect Graphics Hardware after Reboot."
date: 2008-04-27
forum: Multimedia Software
---

### Post by brettnak on 2008-04-27
Hey all,

Some people seem to have had this problem, but the other thread was related to their kernel and having upgraded from Gutsy.  I've installed a fresh copy of Hardy and after I install the proprietary driver, I loose all settings and Ubuntu can't detect my card after I reboot.

Here's what I did:

```

sudo /etc/init.d/gdm stop
sudo sh NV* #ran the installer (169.12)
sudo /etc/init.d/gdm start

```

It works until I reboot.

Thanks

---

### Post by rm249 on 2008-04-27
Exact same thing happens to me, my installation is a new install, I installed the latest drivers from Nvidia (169.12) and did exactly what you did, after rebooting it starts up in low graphics mode. Only way to get it back and working is to reinstall the drivers. I have tried the DISABLED_MODULES="nv nvidia_new" in the linux restricted modules file but did not have any luck at all. (See [http://ubuntuforums.org/showpost.php?p=4795826&postcount=24](http://ubuntuforums.org/showpost.php?p=4795826&postcount=24))

If anyone has figure out a way to fix this it would be greatly appreciated. 

PC Information:
Intel Core 2 Quad Q6600
EVGA nForce 680i Motherboard
EVGA Geforce 8800 GTX Video Card
3GB RAM

Thanks,
Ryan

---

### Post by brettnak on 2008-04-28
Solved

A friend of mine figured there was an init.d script loading the old drivers so this is what I did.  The fix is actually quite simple.  Go into synaptic and search for nvidia.  Remove the package nvidia-kernel-common, either with apt-get or synaptic.  It will remove four other packages, so, I'm assuming some things will not auto-update in the future, however, I'm pretty new to this stuff as well so I don't know exactly what the consiquences of this will be down the line, in any case, removing that packages and the packages that depend on it, then reinstalling the nvidia driver manually will do the trick.

---

