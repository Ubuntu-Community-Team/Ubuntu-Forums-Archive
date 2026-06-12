---
title: "Broadcom STA wireless driver not activating"
date: 2010-09-02
forum: Networking &amp; Wireless
---

### Post by leenuxlee on 2010-09-02
Hello,
I just installed Ubuntu Desktop Edition 32-bit on my Dell Studio 1535 laptop. I generally work with wireless.
My hardware driver is Broadcom STA wireless driver. It is not activating and it tells me to check file  /var/log/jockey.log . I put it in the terminal and this is what comes out
```
bash: /var/log/jockey.log: Permission denied

```
Any help is appreciated,
thank you.

---

### Post by anubhavrocks on 2010-09-02
Try this:
sudo cat /var/log/jockey.log

---

### Post by AndyM3 on 2010-09-02
Did you upgrade your system before trying to install the driver? That usually solves it for me.
If not, run Update Manager (it's in the Administration menu), check for updates and install them. Then run Jockey (Hardware Drivers) again.

---

