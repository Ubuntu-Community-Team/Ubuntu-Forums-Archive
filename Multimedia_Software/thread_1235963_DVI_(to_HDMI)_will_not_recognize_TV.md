---
title: "DVI (to HDMI) will not recognize TV"
date: 2009-08-09
forum: Multimedia Software
---

### Post by Wyldfire on 2009-08-09
I have an Element HDTV connected to a Nvidia 9400 GT video card.  I realize that the TV won't be recognized unless it is on and tuned to the HDMI input.  However, for some reason, the TV won't recognize now at all.  Even with another monitor on the VGA port, the Nvidia driver won't recognize that anything is attached to the DVI port.  The card is only a couple of weeks old, so I doubt it is not working correctly.  Anyone know of any way to force the DVI port to become active?  If this could be activated automatically on boot, that would be even better.  Any ideas?

Thanks

---

### Post by Lantesh on 2009-08-09
Install nvidia-settings if you don't have it already
```
sudo apt-get install nvidia-settings
```

Now run nvidia-settings as root.  You have to run it as root or any changes you make won't be saved.
```
sudo nvidia-settings
```

Now play around in the resulting interface.  You should be able to set things up the way you want, and save it to your xorg.conf file all in this nice GUI.

---

