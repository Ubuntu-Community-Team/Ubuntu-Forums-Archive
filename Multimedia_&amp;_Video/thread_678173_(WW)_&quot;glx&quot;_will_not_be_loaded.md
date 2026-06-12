---
title: "(WW) &quot;glx&quot; will not be loaded"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by fdelpin on 2008-01-25
Hi,

Im running Gutsy 7.10. Tried to update the driver for my video card Nvidia Ge-Force 7400 and didn't work. Now Im traying to revert the changes to go back to the previous version (the one shipped with gutsy, that worked fine but unstable and didn't allow suspend to ram).

I think I did a clean uninstall of the updated version. I installed nvidia-glx-new. I get the module loaded:

lsmod | grep nvidia
nvidia               3932108  0 
agpgart                35016  2 nvidia,intel_agp

But when the xsession starts glx can not be loaded. When I check /var/log/Xorg.0.log I get:

[B][SIZE="2"](WW) "dbe" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "dri" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "glx" will not be loaded unless you've specified it to be loaded elsewhere.
(WW) "vbe" will not be loaded unless you've specified it to be loaded elsewhere.
[/SIZE][/B]
Im using the xorg.conf created by the Nvidia driver. It all works fine if I use nv instead but I get no graphic effects.

Thanks!

---

### Post by bff7755a on 2008-03-27
I has the same problem :(

---

