---
title: "composite extension is not avalible"
date: 2011-10-18
forum: Multimedia Software
---

### Post by martin022 on 2011-10-18
I have nVidia ENGTS250 1GB graphic card, ubuntu 10.04, 2 different monitors (Samsung SyncMaster 2220LM + ACER AL1751).
I need xinerama enabled in nVidia settings but when i click on Extra in visual effects i get this error: "Composite extension is not avalible." Previously I had same spec with ubuntu 10.04 but everything worked perfectly.
How to repair it?

---

### Post by BicyclerBoy on 2011-10-18
[http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/xcompositeextension.html](http://us.download.nvidia.com/XFree86/Linux-x86/275.09.07/README/xcompositeextension.html)
about line 50

- The Composite extension is currently incompatible with Xinerama..

You may have to use an older Xorg & older nVidia driver; This may not be practicable.
Or have to use twinview (or separate X screens).

---

### Post by martin022 on 2011-10-18
thanks for reply. where to download older drivers for xorg?

---

### Post by BicyclerBoy on 2011-10-18
You can force an older version in synaptic package manager..& then lock that version..

If you build your own Xorg you may get into endless dependency issues.

But Xorg Xinerama is dead & can't be resuscitated.
AMD multi-monitor & nVidia twinview added nails to the lid of the coffin.

---

