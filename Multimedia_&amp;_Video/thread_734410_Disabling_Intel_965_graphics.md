---
title: "Disabling Intel 965 graphics"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by astronouth7303 on 2008-03-24
I'm running a desktop with an intel DG965RY mobo (that is, it uses the G965 express chipset with G965 GMCH aka X3000 graphics). I recently bought and installed at video card (NVidia GeForce 8600 GT PCIe). The new video card is installed, configured, and running happy.

My problem is that I can't disable the on-board intel graphics so I can enable things like compiz. If I go into the BIOS and change the graphics to "external PCIe" or "auto", Ubuntu won't finish start-up. The kernel (i think) instead prints what looks like a stack trace for a long time (several minutes before I kill it).

This isn't a problem except that Ubuntu refuses to enable compiz unless all the graphics drivers can use it.

Ubuntu: 7.10, fully updated

---

### Post by Sam Lars on 2008-03-24
If you can boot to the new card and it works fine, you should just install the driver for it through the Restricted Drivers manager.

---

### Post by astronouth7303 on 2008-03-24
> **Sam Lars said:**
> If you can boot to the new card and it works fine, you should just install the driver for it through the Restricted Drivers manager.

> **astronouth7303 said:**
> I'm running a desktop with an intel DG965RY mobo (that is, it uses the G965 express chipset with G965 GMCH aka X3000 graphics). I recently bought and installed at video card (NVidia GeForce 8600 GT PCIe). **The new video card is installed, configured, and running happy.**

Nvidia drivers are working fine.

---

### Post by Sam Lars on 2008-03-24
Good, then it doesn't seem that you need to disable your Intel so much as you need the right drivers for the Nvidia.

---

### Post by astronouth7303 on 2008-03-26
> **Sam Lars said:**
> Good, then it doesn't seem that you need to disable your Intel so much as you need the right drivers for the Nvidia.


Let me clarify:

If i try to enable compiz, tell it to use the drivers, and then open the Displays configuration dialog, it will show that it's attempting to use the nvidia driver with the intel graphics chip.

The nvidia driver can do Compose just fine. i810/intel drivers can't.

---

### Post by Sam Lars on 2008-03-26
So it works fine with regular graphics and the Nvidia card, but Ubuntu gets confused between the two cards when you try to enable Compiz?
What do you get from
```
glxinfo
```
in the terminal?

---

