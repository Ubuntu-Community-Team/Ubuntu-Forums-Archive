---
title: "No Internet connection"
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by crazyfrog1234 on 2009-05-30
Hi ! Can U help me for this problem:
SIOCGMIIPHY on 'eth0' failed: Operation not permitted
SIOCGMIIPHY on 'eth1' failed: Operation not permitted
SIOCGMIIPHY on 'eth2' failed: Operation not permitted
SIOCGMIIPHY on 'eth3' failed: Operation not permitted
SIOCGMIIPHY on 'eth4' failed: Operation not permitted
SIOCGMIIPHY on 'eth5' failed: Operation not permitted
SIOCGMIIPHY on 'eth6' failed: Operation not permitted
SIOCGMIIPHY on 'eth7' failed: Operation not permitted
no MII interfaces found

---

### Post by Iowan on 2009-05-30
I found a [similar]("http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/c613e1eebcf1bc2e") topic. When do you get the error? If you're using **mii-tool** (new one for me) try:```
sudo mii-tool
```

---

### Post by crazyfrog1234 on 2009-05-30
Thanx, I'll try it.

---

