---
title: "getting nvidia driver to work"
date: 2008-10-28
forum: Multimedia Software
---

### Post by scorchgeek on 2008-10-28
I recently upgraded from integrated graphics in my machine to a nice new Geforce 9500. The next time I booted, GNOME would not start. Okay, fine, wrong driver. So I booted into recovery mode and fixed the X server, which dropped me down to the default driver. But how do I get the new driver? Is the Linux driver for it not out yet?

---

### Post by cyfur01 on 2008-10-28
I prefer using EnvyNG, which can be installed via Synaptic Package manager or:```

sudo apt-get install envyng-gtk
``` Once installed, it should be under Applications->System Tools.

This program automatically manages the installation of all the drivers, and I haven't had issues with it yet.

---

### Post by scorchgeek on 2008-10-28
When using it I get the following error:
```
Exception: EnvyNG ERROR: Envy does not recognise your card as compatible with any version of the driver.this might happen because either your card is not supported by the driver or Envy's hardwaredetection failed. You can try the manual installation at your risk.

```
This is in the terminal window that opens upon selecting automatic installation. There's a manual installation option, but I don't know which version to select.

---

### Post by cyfur01 on 2008-10-28
If you want to try the manual driver, go for the newest one (173.X.X). I'm not completely sure if this will work or not, but it's worth a try.

You can also try to find out more at the [EnvyNG homepage]("http://albertomilone.com/nvidia_scripts1.html").

Also, if you're running Hardy, I would suggest that you wait 2 more days until Intrepid is released. It supports a much new driver (177.X.X) which will definitely support the 9000 series. These can be installed then through System->Administrator->Hardware Drivers.

---

### Post by scorchgeek on 2008-10-28
I'll go ahead and try that. I'll let you know if that works.

---

