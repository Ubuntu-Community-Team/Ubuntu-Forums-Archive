---
title: "no nvidia in 2.6.24-16"
date: 2008-04-23
forum: Multimedia Software
---

### Post by dguido on 2008-04-23
2.6.24-15 works just fine, but when I boot into -16, Ubuntu won't load the nvidia module. I know that I have the restricted-modules package installed. I'm using the same xorg.conf when it works and when it doesn't.

What could be the problem?

---

### Post by jtrindle on 2008-04-23
Even though you have the restricted modules installed, they may not be in the path for the new kernel version.

Under System->Administration->Screens and Graphics->Graphics Card->Driver Choose driver by model.  When you choose your NVIDIA card it should offer proprietory as well as open source drivers.

If they don't show up check System->Administration->Restricted Drivers Manager to make sure the NVIDIA drivers are still there.

You may need to re-install the Restricted Driver for NVIDIA even though it is present, to get it copied into the modules directory for the new kernel.

---

### Post by dguido on 2008-04-23
Booting into the non-functioning kernel and running:
```
sudo dpkg-reconfigure linux-restricted-modules-2.6.24-16-generic
sudo dpkg-reconfigure nvidia-glx-new
```

made it work. Don't know why I didn't think of that before. I'm starting to get lazy and frustrated fixing all these minor annoyances in 8.04 *grumble*. Thanks.

---

