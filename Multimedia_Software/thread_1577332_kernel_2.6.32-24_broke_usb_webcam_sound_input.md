---
title: "kernel 2.6.32-24 broke usb webcam sound input"
date: 2010-09-18
forum: Multimedia Software
---

### Post by dingle117 on 2010-09-18
In Lucid, Logitech Pro 9000 webcam worked fine until the kernel was upgraded to
2.6.32-24 recently.  The usb sound was not listed in /proc/asound/cards. I had to boot from 2.6.32-23 to make it work.

UPDATE: the recent upgrade to 2.6.32-25 fixed this problem.

---

### Post by a.daniel on 2010-09-20
My PCI sound card stopped working after upgrade to 2.6.32-24. Following the advice in Bug #605519 [1] fixed the issue for me. It might also solve your issue with the Logitech webcam.

[1] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605519](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605519)

---

### Post by dingle117 on 2010-09-20
> **a.daniel said:**
> My PCI sound card stopped working after upgrade to 2.6.32-24. Following the advice in Bug #605519 [1] fixed the issue for me. It might also solve your issue with the Logitech webcam.

[1] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605519](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/605519)

Thanks, but no, it's not related that bug report. My account's groups has audio.

---

