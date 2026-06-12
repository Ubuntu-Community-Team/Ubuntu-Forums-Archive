---
title: "[SOLVED] [Nvidia][EnvyNG] low resolution with 71.86.04 legacy driver"
date: 2008-06-30
forum: Multimedia Software
---

### Post by BennyLZ on 2008-06-30
Hi.
I had a problem with 3D applications and nvidia-glx driver.
I solved installing legacy driver with envyng. now 3D games work, but with this driver I can't use a resolution higher than 800x600. If I open nvidia-settings, I get this: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." So I run "nvidia-xconfig" as root, and I get "sudo: nvidia-xconfig: command not found".
I need 1024x768.... what can I do? :confused:

edit: my video card is Nvidia Geforce4 MX integrated gpu with 32mb of memory.

---

### Post by BennyLZ on 2008-06-30
Up :(

---

### Post by ubuntu-freak on 2008-06-30
Try executing this command in the terminal:
 
**sudo xrandr -s 1024x768**
 
If that doesn't work, execute the following command:
 
**gksudo displayconfig-gtk** 
 
Next, try changing the screen type from "Default" to "Generic", then see if you can apply the resolution this time.

---

### Post by BennyLZ on 2008-07-01
> **reassuringlyoffensive said:**
> Try executing this command in the terminal:
 
**sudo xrandr -s 1024x768**
 
If that doesn't work, execute the following command:
 
**gksudo displayconfig-gtk** 
 
Next, try changing the screen type from "Default" to "Generic", then see if you can apply the resolution this time.

the second one works! :D
now i have legacy driver (3D finally works) with the right resolution.

but I still have this problem:
> If I open nvidia-settings, I get this: "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server." So I run "nvidia-xconfig" as root, and I get "sudo: nvidia-xconfig: command not found".

if I run ```
sudo nvidia-settings
``` I get this: 
```
ERROR: NV-CONTROL extension version 1.6 is too old; the minimimum required
       version is 1.11.

```

:confused:

EDIT: I solved installing an old (very old) version of nvidia-settings. If someone has a better solution, pls tell me.
thanks!

---

### Post by ubuntu-freak on 2008-07-01
Glad you got your res' problem sorted. You're issue with nvidia-settings may be due to the fact that you're having to use the legacy driver.

---

