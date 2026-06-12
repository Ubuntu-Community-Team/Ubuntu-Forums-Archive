---
title: "Ati driver install with 2.6.33 kernel"
date: 2010-05-27
forum: Multimedia Software
---

### Post by kamina on 2010-05-27
I received a new workstation today, and installed ubuntu (10.4 i386) on it. One of the first things I did was to upgrade the kernel to the 2.6.33 tree as I have a ssd drive (and it will have a lot of writes / deletes). I installed the kernel from the location mentioned in most tutorials here along with the headers and source. However after this accepting the proprietary ati drivers caused big problems. They would not install, and actually blocked me from installing anything else. 

I had not spent a lot of time on the install so I just started fresh. This time I directly accepted the proprietary driver and all went fine. However I'm wondering if the newer kernel tree would break the graphics drivers again... Has anyone installed both? I really need Trim support. 

I hope the description is sufficient, I'm at home now so can't dig anything out of the machine.

---

### Post by kamina on 2010-05-27
Seems you need to patch the driver for it to work with > 2.6.32 kernel tree.

[http://www.phoronix.com/forums/showthread.php?t=23463](http://www.phoronix.com/forums/showthread.php?t=23463)

---

