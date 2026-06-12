---
title: "How do I make NTop not start at boot?"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by matt4522 on 2011-01-20
I have installed ntop and it works fine, but I do not use it every day. Somehow it installed to start on boot. I do not want it to start automatically at system start/boot. I looked and searched, and looked some more but I can not figure out how to stop it from starting at boot time. I'm using Unbuntu 10. Please help!

---

### Post by notfixingit on 2011-02-08
sudo update-rc.d ntop disable

---

