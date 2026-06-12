---
title: "Networking not working after kernel update"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by JMazzy on 2013-01-18
Earlier I installed the kernel update (from 3.5.0-21 to 3.5.0-22) in xubuntu 12.10 and my system stopped recognizing any networking (ran ifconfig via terminal and it only showed the loopback, no ethernet or wireless). I reverted to the old kernel (3.5.0-21) and it works again. Is there something I need to do to get networking working with the new kernel?

edit: Thanks to leef's suggestion to use lsmod, I compared the two and realized the proprietary drivers for both my ethernet controller and wireless adapter were removed by the kernel update. I reinstalled them and now everything works fine.

---

### Post by leef on 2013-01-18
please could you provide the output of the following command for both kernels?

```
lsmod
```

---

### Post by dannyboy79 on 2013-01-18
sometimes kernel upgrades have kernel module regressions in them on accident due to fixing other things they accidentally break something totally not related.

you could file a bug so that it gets fixed.

---

### Post by JMazzy on 2013-01-18
Thanks to those who responded. See edit to my post - it looks like I needed to reinstall networking drivers for some reason. Is there a way to keep them through a kernel update? I'm new to Linux/Ubuntu so I don't know if this is a common issue or not.

---

### Post by leef on 2013-01-18
> **JMazzy said:**
> edit: Thanks to leef's suggestion to use lsmod, I compared the two and realized the proprietary drivers for both my ethernet controller and wireless adapter were removed by the kernel update. I reinstalled them and now everything works fine.

It's so good when people work these things out on their own, rather than just copying and pasting, nice work buddy.

---

