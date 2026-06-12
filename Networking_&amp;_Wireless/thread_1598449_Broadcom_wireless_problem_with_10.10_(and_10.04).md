---
title: "Broadcom wireless problem with 10.10 (and 10.04)"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by GhostCoder on 2010-10-16
My problem is that after reboot I need to remove and install again the restricted driver for BCM4312. It works perfectly until I reboot. After reboot it is "active but not in use" according to the restricted drivers manager. What is wrong? This happens on 10.10 and it happened also on 10.04. Previously I was running Linux Mint 7 on the same hardware and it worked without any problems. The kernel seems to be 2.6.32-25-generic.

---

### Post by GhostCoder on 2010-10-16
> **GhostCoder said:**
> My problem is that after reboot I need to remove and install again the restricted driver for BCM4312. It works perfectly until I reboot. After reboot it is "active but not in use" according to the restricted drivers manager. What is wrong? This happens on 10.10 and it happened also on 10.04. Previously I was running Linux Mint 7 on the same hardware and it worked without any problems. The kernel seems to be 2.6.32-25-generic.


I got it working by adding wl to /etc/modules.

---

### Post by eztothink on 2010-10-19
Could you please explain more ??how to fix it?
i can't understand " Wl to /ect/modules"
i'm the beginner...

---

### Post by squizzi on 2010-10-19
> **eztothink said:**
> Could you please explain more ??how to fix it?
i can't understand " Wl to /ect/modules"
i'm the beginner...

```
sudo gedit /etc/modules
```

Add wl to the end of this config file and save and exit.

---

