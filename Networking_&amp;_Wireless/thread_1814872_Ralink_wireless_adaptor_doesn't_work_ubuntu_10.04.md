---
title: "Ralink wireless adaptor doesn't work ubuntu 10.04"
date: 2011-07-30
forum: Networking &amp; Wireless
---

### Post by nocco on 2011-07-30
Hi, I've ubuntu 10.04 and I can't connect to router wi-fi with my new wireless adaptor usb (ralink 2870). I've tried various guides but nothing. The adaptor work fine with Windows and other linux distributions. Please help me

---

### Post by chili555 on 2011-07-30
Let's see what you have. Please open a terminal and run and post:```
lsusb
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by nocco on 2011-07-30
Thanks a lot chili555.
But after few months, I've found the solution whit this fantastic guide:

[http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html](http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html)

---

### Post by nocco on 2011-07-30
How can I put SOLVE in this thread? thanks

---

### Post by chili555 on 2011-07-30
> **nocco said:**
> How can I put SOLVE in this thread? thanksUse thread tools at the top and Mark Solved.

I believe only the blacklist step is required in Natty 11.04.

---

### Post by ratcheer on 2011-07-30
Click on the Thread Tools link near the top right of the thread.

Tim

---

