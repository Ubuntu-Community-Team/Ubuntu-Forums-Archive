---
title: "Acer Nplify under ubuntu 11.04"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by raulv on 2011-04-30
hi there!

i'm having a problem with my acer 5742.

Wifi actuallly works, but if i test the speed, it won't go over 3 Mbs, and my bandwith should be around 50 Mb.

Anyone elese got this problem ?

Raul.-

---

### Post by thebobarian on 2011-08-04
Having this same problem too? Find a solution?

---

### Post by raulv on 2011-08-04
> **thebobarian said:**
> Having this same problem too? Find a solution?

This should work:

```
sudo -s
 echo "options ath9k nohwcrypt=1" > /etc/modprobe.d/ath9k.conf
 reboot

```If not, try installing latest kernel.

---

