---
title: "Changed Computer - Video Problem"
date: 2011-02-14
forum: Multimedia Software
---

### Post by Ingla on 2011-02-14
Hello.

I'm running Ubuntu 10.04.

I've changed computers. 

Previously using nVidia graphics card with proprietary driver.

This computer has an ATI (radeon)card.

In /etc/X11, I have an xorg.conf.backup, three numbered xorg.conf.backup files and a xorg.conf.failsafe file.  There is no xorg.conf.

I suppose Ubuntu is booting using the failsafe file, which says the driver in use is fbdev.

Can't get the right resolution.

Since Ubuntu took away the xorg reconfigure method, I'm not finding a way to make it recognize that it's running an ATI card and should use an appropriate driver (radeon?).

Is there any way to get back to just a xorg.conf and it's backup, properly configured so I can get the correct resolution?


Thanks.

---

### Post by fsleeman on 2011-02-14
You probably won't have much luck until you install an ATI driver, either an open source or proprietary one. The default drivers with Ubuntu won't give you all of the display setting you want.

---

### Post by Ingla on 2011-02-15
Some people seem to recommend a driver called fglrx, which can be installed from Synaptic.

Will simply installing it make Ubuntu use it?

---

