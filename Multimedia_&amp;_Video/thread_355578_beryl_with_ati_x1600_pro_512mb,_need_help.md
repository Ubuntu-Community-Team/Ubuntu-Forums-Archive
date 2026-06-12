---
title: "beryl with ati x1600 pro 512mb, need help"
date: 2007-02-07
forum: Multimedia &amp; Video
---

### Post by pronto185 on 2007-02-07
For the past few days I have been trying to get beryl working, and so far no luck
i have an ATI Radeon X1600 pro 512 MB,   pci express graphics card

When i select it to use the beryl window managers it crashes and goes back to my XFCE window manager

when i type beryl into terminal i get this 
```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

```


anyone have any ideas to get this working?

thanks

---

### Post by Bram77 on 2007-02-07
I have the axact same problem with my x800 GTO2 using the fglrx driver.

---

### Post by hackeron on 2007-02-14
same here ;(

---

### Post by Datalanche on 2007-02-14
The fglrx driver does not support AIGLX. If you want to get beryl working under it, you will have to use an XGL method, or the open source radeon driver, provided you have an older card that has working 3D support in it(X800 and below I believe).

---

