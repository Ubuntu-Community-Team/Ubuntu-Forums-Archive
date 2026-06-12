---
title: "Password prompt on reconnect to wireless ap"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by kerryhall on 2013-05-19
Hello folks,

I have the same problem as:
[http://ubuntuforums.org/showthread.php?t=1041144](http://ubuntuforums.org/showthread.php?t=1041144)

But it looks like that thread is closed. I have tried ticking the box marked "Available to all users" but that didn't help. My ap/router/modem crashes probably 5-10 times a day (I can tell because everyone in my house gets disconnected) and every time I reconnect I am prompted for my password. This occurs on two different systems, one running 12.04.1 and one running 12.04.2.

Thanks!

---

### Post by Whoopie on 2013-05-20
This is fixed in latest NetworkManager (e.g. in Ubuntu 13.04). If you use 12.04, you could use my NM package where I backported the patches, see [here]("https://launchpad.net/~whoopie79/+archive/ppa/+packages").

---

