---
title: "Fatal Modprobe Errors On Boot 2.6.35"
date: 2010-10-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by NightwishFan on 2010-10-04
This happens both on Maverick and Lucid with the Maverick kernel.

I get a message along the lines of:
```
modprobe: FATAL: Could not load /lib/modules/2.6.35-22-server/modules.dep: No such file or directory
```

It seems to delay boot a bit however that might be a placebo. Nothing seems to be wrong and the logs show no issue though.

---

### Post by drmartens on 2010-10-04
It seems to be a bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642421)

I see the same after installing RC.

---

### Post by NightwishFan on 2010-10-04
Ok, thanks for the confirmation and the link.

---

