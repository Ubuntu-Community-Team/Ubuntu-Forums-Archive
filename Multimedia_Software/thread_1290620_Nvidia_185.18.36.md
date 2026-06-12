---
title: "Nvidia 185.18.36"
date: 2009-10-13
forum: Multimedia Software
---

### Post by Somenoob on 2009-10-13
1) Using two 8800GT cards through SLI
2) Installed 185.18.36 successfully but GDM hangs at battery state 
3) I put SLI on, got nothing.

Any ideas?

---

### Post by Somenoob on 2009-10-13
Bump, any help is appreciated.

---

### Post by beastrace91 on 2009-10-13
Does it work on other driver versions? I know the newer (beta) drivers have been adding better SLI support as well as newer cards. Maybe try something from the 190.xx series?

~Jeff

---

### Post by lovinglinux on 2009-10-14
It's a reported bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/421442](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/421442)

To fix the unbootable situation, log in a LiveCD session, backup and delete /etc/X11/xorg.conf, then reboot.

BTW, please don't bump the thread so fast. You should wait at least 24 hours to do so.

---

### Post by lovinglinux on 2009-10-14
This bug has been fixed with the latest updates! =D>

---

### Post by Somenoob on 2009-10-16
> **lovinglinux said:**
> This bug has been fixed with the latest updates! =D>

The recent updates didn't do anything for me. Any config issues I should know about 180*?

---

