---
title: "SSB respawning after boot"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by urielgm on 2010-01-10
I installed karmic on a friends laptop (hp 1225dx) that uses a broadcom 4312 wireless card The documentation on installing the wireless driver was excellent and i was able to install it easily. However, after reboot ssb would not let the newly installed wl driver.

I tried different things such as in [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218763](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/218763) , but nothing worked. Finally, I went to my /etc/init.d to find  the file wirelessfix.sh. As it turns out this file was calling b44 and ssb. I changed the file to install the wl.ko file and got the wireless working.

---

