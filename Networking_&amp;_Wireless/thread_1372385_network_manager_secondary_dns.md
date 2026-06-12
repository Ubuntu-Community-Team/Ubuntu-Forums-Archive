---
title: "network manager secondary dns"
date: 2010-01-04
forum: Networking &amp; Wireless
---

### Post by rick71 on 2010-01-04
Is it possible to have a secondary DNS listed in Network Manager applet, and if so, how?

Any and all help appreciated.

---

### Post by gs777 on 2010-01-04
just add the secondary dns after a comma.like--8.8.8.8,8.8.4.4

---

### Post by rick71 on 2010-01-04
Thanks, I'll give that a try.

---

### Post by Iowan on 2010-01-04
If it doesn't work, try space - comma - space.

---

### Post by rick71 on 2010-01-04
The secondary DNS is now listed in the Network Manager, but it didn't take until I restarted. I looked in resolv.conf, and only one DNS IP was listed, even after I did a /etc/init.d/networking restart.

Anyone know why the networking restart didn't re-write the resolv.conf, and why I had to restart?

---

### Post by Iowan on 2010-01-04
Networking restart might not restart Network Manager.

---

### Post by rick71 on 2010-01-04
How do I restart the network manager applet?

---

### Post by Iowan on 2010-01-04
On Karmic, it's an Upstart job, but there's a link in /etc/init.d so this *might* work:```
/etc/init.d/network-manager restart
```

---

### Post by rick71 on 2010-01-05
Thanks...
I'm using Jaunty, and NetworkManager (that's how it is spelled) is there. I'll give the /etc/init.d/NetworkManager a try the next time I need to restart it.

---

