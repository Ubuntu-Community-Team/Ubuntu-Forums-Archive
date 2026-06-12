---
title: "How did you installed your ATI Radeon 9600 (Not Mobility) Drivers?"
date: 2008-08-07
forum: Multimedia Software
---

### Post by syms on 2008-08-07
Please say that, I tried many ways, but they didn't worked. So how did you maked that your Radeon 9600 with poprietary worked?

---

### Post by Cygoku on 2008-08-07
The easiest way to install any version of the ATI driver, imo, is to use the application named Envy.  If you are using Hardy Heron, you can install it trough "Synaptic Package Manager".  I suggest you enable the "Proposed Updates" repository trough "Software Sources" to be able to install the 8.06 ATI driver.  If not, you will only be able to install the 8.03 version.  8.06 will give you a lot of video playback improvement.

Cygoku

---

### Post by syms on 2008-08-07
thank, but when envy installs driver, i reboot pc and x dont loads.

---

### Post by jocko on 2008-08-07
Could you post your /etc/X11/xorg.conf?
```
gedit /etc/X11/xorg.conf
```
Do you use hardy or gutsy?
Which version of the driver have you tried installing?

When Xorg does not start after you have installed with envy, do you get any error messages?
Exactly how does it not start? Do you get a safe graphics gnome session? Do you get the displayconfig tool? Do you get the gdm login screen? Or does it just kick you back to a terminal?

Have you tried to install the driver from the repo? First uninstall the envy version (not sure how that's done, but I guess you do it from envy), then install the package xorg-driver-fglrx from synaptic.

---

