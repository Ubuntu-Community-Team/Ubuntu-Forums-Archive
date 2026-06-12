---
title: "which video driver is being used?"
date: 2009-07-19
forum: Multimedia Software
---

### Post by puccaso on 2009-07-19
if i delete the xorg.conf
X is supposed to autodetect my systems capabilities and render an xorg on the fly
but how do i find out which graphics driver is being used?

---

### Post by mikewhatever on 2009-07-19
In case you use Intrepid or Jaunty, xorg.conf is nearly empty, and if you delete it, it will probably get regenerated on reboot.
You can find out what graphics driver is in use with the following command:
**sudo lshw -C display | grep driver**.

---

