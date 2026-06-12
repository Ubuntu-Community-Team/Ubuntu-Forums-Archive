---
title: "wireless expresscard recommendations?"
date: 2011-01-11
forum: Networking &amp; Wireless
---

### Post by db2k on 2011-01-11
after about 3 12 hour days of messing with it, i'm nearly positive there is no way the onboard broadcom wireless is going to work. (it's an hp dv9000 running ubuntu studio 10.4)

can someone recommend a wireless express card that will work out the box with no troubles?

thanks!

---

### Post by PatchesTheCaveman on 2011-01-12
There are some suggestions here:
[http://tuxmobil.org/expresscard_linux.html](http://tuxmobil.org/expresscard_linux.html)

---

### Post by cchhrriiss121212 on 2011-01-14
No wireless card will work out of the box with Ubuntu Studio as it is designed with no wireless capability. Essentially the studio developers decided to remove gnome-network-manager from the build as it interfered with audio processing.
If you want to use studio with wireless, plug in to a wired connection and install network manager.

---

