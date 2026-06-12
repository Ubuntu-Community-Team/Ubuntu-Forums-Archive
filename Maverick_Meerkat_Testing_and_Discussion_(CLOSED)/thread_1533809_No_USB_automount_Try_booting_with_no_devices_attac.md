---
title: "No USB automount? Try booting with no devices attached."
date: 2010-07-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2010-07-18
After spending a few hours (OK, more than a few) tracking down why my USB drives weren't automatically being mounted by nautilus I eventually tried a clean install. This didn't fix it. However, when I compared my Maverick VM and my Maverick laptop the main difference was the presence of a USB mouse and keyboard that had been plugged in since the install.

I unplugged them, and everything that didn't work now worked (Disk Utility aka palimpsest). After a reboot automounting also worked again.

For more, see here:
[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/435136](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/435136)

---

