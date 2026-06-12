---
title: "[Q][Problem]No OpenGL on Intel GMA"
date: 2012-02-29
forum: Multimedia Software
---

### Post by mtotho on 2012-02-29
Hello,

I have recently installed Ubuntu 11.10 on my Asus U35JC.

This laptop has BOTH an Nvidia Geforce 310 and "Intel GMA HD"
(I cannot for the life of me determine any specific GMA model.. the chipset is intel HM55)

At first I had installed the nvidia drivers. I soon realize that my battery was dying EXTREMELY quickly. I installed the Nvidia Bumblebee drivers

At First typing
```
lspci | grep Graphic

```

yielded:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2) (prog-if 00 [VGA controller])

```

After installing and configuring bumblebee.. I can disable the Nvidia card like this.
```
tee /proc/acpi/bbswitch <<<OFF

```

And the ```
lspci | grep Graphic

```
yields this after
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)

```

which has significantly increased my battery life and disabled the unwanted nvidia card, but now ```
glxinfo
```
displays

```
name of display: :0
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Error: couldn't find RGB GLX visual or fbconfig

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".

```

Any information on how to install proper intel drivers for this card? I believe they are already installed by default, but maybe need to be reconfigured now that I am no longer using the Nvidia?

Thanks in advance,

mike

---

### Post by Yellow Pasque on 2012-02-29
The intel drivers are installed by default. If you installed nvidia drivers, that's why the intel isn't working (because nvidia uses proprietary libGL and libglx).

---

