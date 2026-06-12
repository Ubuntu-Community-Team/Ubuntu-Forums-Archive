---
title: "Linux is really slow to connect"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by kogger on 2009-09-05
I recently posted a topic about being unable to consistently initialize a new native Linux module for my Broadcom STA wireless driver, but I managed to solve that problem by adding "wl" to /etc/modules. However, doing this hasn't solved the problem I was hoping to correct by switching over from ndiswrapper to a native driver in the first place: Ubuntu is really slow to actually get a connection, and generally tells me that it's failed a couple times first. I dual-boot with XP, and Windows has no problem connecting within just a few seconds, but Ubuntu takes a lot longer.

Since switching from ndiswrapper didn't solve the problem, what else could be causing Ubuntu to go so slowly compared to Windows?

---

