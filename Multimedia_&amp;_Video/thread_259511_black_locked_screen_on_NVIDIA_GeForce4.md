---
title: "black locked screen on NVIDIA GeForce4"
date: 2006-09-17
forum: Multimedia &amp; Video
---

### Post by marioquark on 2006-09-17
hi,
i've removed any precompiled nvidia kernel debian driver, i've purged and reinstalled the official nvidia script... X log is clean (no EE error)  but X server didn't start and screen is locked in black (i also tried a lower bit resolution, but nothing...).
i set DISABLED_MODULES="nv" in /etc/default/linux-restricted-modules-common as nvidia forum tells.

what can i do?! :(

---

### Post by tseliot on 2006-09-17
Try envy:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

if that doesn't work try point 4 of the Problems Section of my guide (even if the description of the problem doesn't match yours):
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

### Post by marioquark on 2006-09-17
ok, script run correctly but nothing... then i tried some options in modprobe.d/option and xorg.xconf in your guide and (after 2 years...) the 3d goes!!!
thank you (it's italian power ;) )

anyway: i have this error:
```
(EE) NVIDIA(0): Failure reading maximum pixel clock value for display device
(EE) NVIDIA(0):     TV-0.
```
any suggestion?

---

### Post by marioquark on 2006-09-18
up! :confused:

---

### Post by tseliot on 2006-09-18
> **marioquark said:**
> ok, script run correctly but nothing... then i tried some options in modprobe.d/option and xorg.xconf in your guide and (after 2 years...) the 3d goes!!!
thank you (it's italian power ;) )

anyway: i have this error:
```
(EE) NVIDIA(0): Failure reading maximum pixel clock value for display device
(EE) NVIDIA(0):     TV-0.
```
any suggestion?

Does that error cause you a problem?

---

