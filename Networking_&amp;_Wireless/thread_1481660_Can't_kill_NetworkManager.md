---
title: "Can't kill NetworkManager"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by Diego Garcia Mendoza on 2010-05-12
Hi, I'm using ubuntu 10.04 and I'm trying to do some tests with aircrack. I've been doing this since Jaunty.

But now when i unload and reload my module ath5k, something is setting my wireless interface in managed mode.

I suspect is NetworkManager but when i try to kill this process (using -9 parameter) it restarts. 

Any idea on how to kill it or which process is starting it over and over again ?

---

### Post by Diego Garcia Mendoza on 2010-05-13
i did it
```
sudo service network-manager stop
```

---

### Post by prosist on 2011-10-16
> **Diego Garcia Mendoza said:**
> i did it
```
sudo service network-manager stop
```

thanks

---

### Post by Rubi1200 on 2011-10-16
Thread closed.

Reason: necromancy

Thanks to all for participating.

---

