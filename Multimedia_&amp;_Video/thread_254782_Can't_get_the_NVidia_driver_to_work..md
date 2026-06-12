---
title: "Can't get the NVidia driver to work."
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by apoth on 2006-09-10
This appears to be the relevant bit of the xorg log file:

> (EE) NVIDIA(0): Version mismatch detected between the NVIDIA X driver and the
(EE) NVIDIA(0):     NVIDIA GLX module.  X driver version: 1.0-8774; GLX module
(EE) NVIDIA(0):     version: 1.0-8762.  Please try reinstalling the NVIDIA
(EE) NVIDIA(0):     driver.
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly.

Seems fairly obvious what the cause is - but how do I fix it? I've tried uninstalling and reinstalling, apt-get update, using different servers in my sources.list, using the envy script... any ideas?

Thanks

---

### Post by tseliot on 2006-09-10
Try Envy:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

use the uninstall function and the install function

---

### Post by apoth on 2006-09-11
Ah I think I had an old envy version. All working now thanks :)

---

