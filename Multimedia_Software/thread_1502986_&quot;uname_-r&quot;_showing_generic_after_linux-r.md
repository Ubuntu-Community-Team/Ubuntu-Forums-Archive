---
title: "&quot;uname -r&quot; showing generic after linux-rt install"
date: 2010-06-06
forum: Multimedia Software
---

### Post by madnessjack on 2010-06-06
Hi guys and girls,

I've been trying to upgrade Lucid desktop into Studio. So far I've managed to get the Ubuntu Studio packaged on, and I've gone through everything on the page [https://help.ubuntu.com/community/HowToVanillaKernelWithRealtimePreemption](https://help.ubuntu.com/community/HowToVanillaKernelWithRealtimePreemption) (so the basic "apt-get install ubuntustudio-..." and "apt-get install linux-rt")

However, when I type "uname - r" it's still showing a generic kernel. Is there something else I need to do?

Many thanks

---

### Post by aeiah on 2010-06-06
grub is still booting the previous kernel. when you upgrade kernels, grub is usually updated to boot using the most recent, but the rt kernel isn't really an upgrade of the other one, and installing it probably didn't add it to grub.

have a look at the grub2 docs to see how to add it and whatnot. it may just be as simple as ```
sudo update-grub
```

---

### Post by madnessjack on 2010-06-07
> **aeiah said:**
> grub is still booting the previous kernel. when you upgrade kernels, grub is usually updated to boot using the most recent, but the rt kernel isn't really an upgrade of the other one, and installing it probably didn't add it to grub.

have a look at the grub2 docs to see how to add it and whatnot. it may just be as simple as ```
sudo update-grub
```

Thank you, you were quite right, worked like a charm!

I can get back to my recording now :)

---

