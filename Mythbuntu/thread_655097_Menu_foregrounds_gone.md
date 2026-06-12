---
title: "Menu foregrounds gone"
date: 2007-12-31
forum: Mythbuntu
---

### Post by rkand on 2007-12-31
Is there a config file I can modify to return to Qt menu rendering? I switched to OpenGL and ever since I can't see the text & pictures that make up the foreground.

---

### Post by Ngiri on 2008-01-01
I had the same problem although the cause may have been different.  I discovered that the system had switched from the Nvidia driver to the vesa driver.  Turning the Nvidia driver back on in the Mythbuntu Control Centre fixed things for me.

---

### Post by rkand on 2008-01-01
I think you're right, because my driver is set to the vesa driver also.  Unfortunately my 8500GT doesn't seem to be supported, everytime I select the driver and reboot, I come back into 'safe mode'.  I guess I'll have to fiddle around with it more.

---

### Post by laga on 2008-01-01
> **rkand said:**
> Is there a config file I can modify to return to Qt menu rendering? 


You can run ```
mythfrontend -O ThemePainter=qt
``` Then, go into the settings menu and make the setting permanent. ```
mythfrontend --reset
``` might work as well.


mythfrontend --help says:
```

-r or --reset                  Resets frontend appearance settings and language
```

---

