---
title: "WPA2 Enterprise doesn't work after upgrade to 12.10"
date: 2013-03-03
forum: Networking &amp; Wireless
---

### Post by pinhas on 2013-03-03
Hi,

I recently upgraded my Lenovo X301 from Ubuntu 11.10 to Ubuntu 12.10 by doing a fresh install. After the installation, my campus wifi, which uses WPA2 Enterprise, no longer works. 

I can still log on to the campus network from my Android phone. And I was able to log on to the campus network with my laptop before upgrading. And I can still log on to other networks such as my home network from my laptop after uprgrading. But for some reason I can no longer log onto the campus WPA2 Enterprise network after the new Ubuntu install.

Any ideas what the problem could be, and how to fix it?

---

### Post by pinhas on 2013-03-03
Oops, I feel kind of stupid but I just found the problem after a week without wifi at work: I just had to change the authentication setting from the default of "Tenneled TLS" to "PEAP" and it works.

---

