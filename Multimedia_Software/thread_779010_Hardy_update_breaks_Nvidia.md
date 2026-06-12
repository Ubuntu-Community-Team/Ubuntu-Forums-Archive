---
title: "Hardy update breaks Nvidia?"
date: 2008-05-02
forum: Multimedia Software
---

### Post by Xer0441 on 2008-05-02
ARGH!

After streamline upgrading from feisty to hardy, my proprietary Nvidia drivers bit the dust. 

The failsafe display manager loads up, but after selecting the video driver I get a failure message. Manually editing xorg.conf to use the nvidia driver and restarting X, I get nowhere. I've uninstalled and reinstalled the drivers (tried with envy and from scratch) and I just can't seem to be getting anywhere.

sudo modprobe nvidia returns:

FATAL: Error running install command for nvidia 


I can't seem to find much info on this, anyone have a clue as to whats going on?

---

### Post by oscarsfriend on 2008-05-02
If you installed your nvidia drivers from the nvidia website, you will need to reinstall them.  They are compiled against the kernel, and the upgrade installed a new kernel, so they will need to be recompiled.

---

### Post by Xer0441 on 2008-05-02
I have used the Nvidia drivers from the site. Re-compiled and even let it build my xorg.conf file. Negative effect in any sense.

---

