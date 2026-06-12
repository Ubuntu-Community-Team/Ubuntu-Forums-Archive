---
title: "Where is my Xorg.conf"
date: 2010-08-26
forum: Multimedia Software
---

### Post by IronArjen on 2010-08-26
I want to install the NVIDIA drivers in order to support Bigscreen. As a first step I wanted to make a backup of my Xorg.conf. It is not there?
It is supposed to be in etc/X11 or not? Did something change in Lucy?

---

### Post by chronozphere on 2010-08-26
Please try:

```

locate xorg.conf

```Here in 9.10, it's still in /etc/x11. :?

---

### Post by sydbat on 2010-08-26
> **IronArjen said:**
> I want to install the NVIDIA drivers in order to support Bigscreen. As a first step I wanted to make a backup of my Xorg.conf. It is not there?
It is supposed to be in etc/X11 or not? Did something change in Lucy?I don't think Lucid uses xorg.conf. You can create it, if needed.

---

### Post by IronArjen on 2010-08-26
It depends on the machine. I run an Intel-Nvidia and locate xorg.conf yields 

/usr/lib/X11/xorg.conf.d
/usr/lib/X11/xorg.conf.d/05-evdev.conf
/usr/lib/X11/xorg.conf.d/10-synaptics.conf
/usr/lib/X11/xorg.conf.d/10-vmmouse.conf
/usr/lib/X11/xorg.conf.d/10-wacom.conf
/usr/share/man/man5/xorg.conf.5.gz

Hence it does not exist.
Is it as if it has been arranged differently

A machine next to mine runs AMD-ATI and DOES have the normal setting in etc

---

### Post by Grenage on 2010-08-26
xorg.conf is legacy, and no longer essential.

Proprietary software from ATI/Nvidia (nvidia-settings etc.) does create one if you specify settings.  It **will** get used if it exists.

---

