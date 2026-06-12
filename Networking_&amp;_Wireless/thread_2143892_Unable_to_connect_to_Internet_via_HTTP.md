---
title: "Unable to connect to Internet via HTTP"
date: 2013-05-10
forum: Networking &amp; Wireless
---

### Post by Don Fulgencio on 2013-05-10
Hello,

I'm trying to fix a student's netbook. It's unable to open any website via HTTP, but HTTPS seems to work just fine. I have two similar netbooks, both with the exact same system installed, but I cannot find any differences in their network configuration.
I've already tried reinstalling Firefox. I tried installing another browser.  ufw is inactive. This is beyond my scope. Can anyone assist me? Thank you.

---

### Post by linuxtechguy on 2013-05-10
Is port 80 being blocked in the firewall?

To check the rules you can do:

```

iptables -L -v -n

```

---

