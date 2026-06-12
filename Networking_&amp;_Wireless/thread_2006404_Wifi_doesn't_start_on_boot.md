---
title: "Wifi doesn't start on boot"
date: 2012-06-19
forum: Networking &amp; Wireless
---

### Post by anandamide on 2012-06-19
Well this is a strange one.

Seemingly out of the blue, my desktop doesn't start networking on boot, presents me with a 'Ubuntu experienced an internal error' message.

It's easily resolved with```
 /etc/init.d/network-manager start
```, but has anyone else experienced similar / have any clue what might be playing up?

---

### Post by nothingspecial on 2012-06-20
*Thread moved to **Networking & Wireless**.*

---

### Post by anandamide on 2012-06-23
Bump

---

### Post by Kakers on 2012-06-27
Hi anandamide, I'm having the same problem, I believe it's a bug.
There is currently a bug raised on [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/950662](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/950662)

---

### Post by anandamide on 2012-07-08
Thanks, but I'm not sure that's my issue.

I've had that bug ('waiting for network connection' on boot)for a while now, but previously my wireless / networking would be up and running once I've logged in. It's only recently that I've had to manually start networking.

---

