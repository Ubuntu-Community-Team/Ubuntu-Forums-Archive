---
title: "Default refresh rate chosen for 800x600 is unsupported by new monitor"
date: 2009-07-30
forum: Multimedia Software
---

### Post by AmyRose on 2009-07-30
I just bought a Dell E170S monitor. It works great, except that the default refresh rate my NVidia GeForce 6100 chooses for the 800×600 resolution (when a game wants that resolution) is not supported by this monitor. Is there any way to force a particular video mode to a different refresh rate (such as when a game like SuperTux 2 requests it)?

This monitor does support 800×600 if I set it to a particular refresh rate (tested both in NVidia's tool and the GNOME tool.)

---

### Post by AmyRose on 2009-08-01
Ah, solved the issue after searching it on nvnews.net!

For anyone else having this trouble on NVidia, add this to your /etc/X11/xorg.conf in the Device section:
```
Option "ModeValidation" "NoXServerModes"
```

Then restart X.

---

