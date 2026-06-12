---
title: "Geforce MX4000 lubuntu 12.10 can't install"
date: 2013-01-07
forum: Multimedia Software
---

### Post by mumia55 on 2013-01-07
I have installed lubuntu 12.10 on this pc which has the respective mx 4000 geforce video card.

but can't install drivers of nvidia, I've tried to look on google, but didn't find any solution that solved my problem.

I already tried to install the legacy drivers from nvidia (NVIDIA-Linux-x86-96.43.23-pkg1), with no success, it makes my screen go to 640x480 resolution...

I want to run Blender on this PC, and it gives me this message (this could be of some help):

./blender
connect failed: No such file or directory

Error: No valid "startup.blend", fall back to built-in default.

Xlib:  extension "GLX" missing on display ":0".
intern/ghost/intern/GHOST_WindowX11.cpp:197: X11 glXQueryVersion() failed, verify working openGL system!
initial window could not find the GLX extension, exit!

help?

---

### Post by Yellow Pasque on 2013-01-07
Nvidia has not updated their 96.xx series drivers for Xserver 1.13, so I would highly recommend installing Lubuntu Precise/12.04, which uses Xserver 1.12. If you install precise, you can pull the nvidia-96 driver right from the repo instead of downloading it.

The other possible solution is downgrading the Xserver using this repo: [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)
Don't install the fglrx driver, of course. You're only interested in the X packages. Note that this is a hack and the Precise/12.04 solution is safer.

---

### Post by mumia55 on 2013-01-07
can I downgrade from lubuntu 12.10 to 12.04?

---

### Post by Yellow Pasque on 2013-01-07
> **mumia55 said:**
> can I downgrade from lubuntu 12.10 to 12.04?
No, but you can try downgrading the Xserver if doing a fresh install of 12.04 is problematic.

---

### Post by mumia55 on 2013-01-07
> **Temüjin said:**
> No, but you can try downgrading the Xserver if doing a fresh install of 12.04 is problematic.

I just wanted to know if it was possible. But I will install 12.04...

---

### Post by Dilutu on 2013-01-10
I just installed nvidia 96 drivers on 12.04 xubuntu from here:
[http://www.ubuntuupdates.org/package/core/precise/restricted/proposed/nvidia-96]("http://www.ubuntuupdates.org/package/core/precise/restricted/proposed/nvidia-96"). No more freezes yet for me.
Th.

---

