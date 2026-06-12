---
title: "Sun Secure Global Desktop - Failed to install SGD client"
date: 2012-12-17
forum: Networking &amp; Wireless
---

### Post by dominion_vortar on 2012-12-17
Hi,

I'm trying to use the Sun Secure Global Desktop, and have installed JDK 7, but when I try to login, I get a window popping up saying "Failed to install SGD client", and it doesn't do anything else.

Has anyone experienced this, or know of a workaround? I'm using Ubuntu 12.04.

Thanks for your time.

---

### Post by deanydean on 2012-12-17
If you're using 64-bit Ubuntu you'll need to install the ia32-libs package as the SGD client is a 32-bit application:

```
$ sudo apt-get install ia32-libs
```Once this is installed, login to SGD and the client should start.

Hope this helps,

-- DD

---

### Post by dominion_vortar on 2012-12-24
Hi,

Apologies for the late reply, I've been away and haven't had a chance to check the forums. Your solution was spot on, thanks very much for your help!

John

---

### Post by raghavendra2 on 2013-09-30
it worked in ubuntu..what do you do on windows? 

Thanks in advance!

---

