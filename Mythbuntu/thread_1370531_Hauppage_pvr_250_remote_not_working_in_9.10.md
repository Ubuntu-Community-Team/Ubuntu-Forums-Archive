---
title: "Hauppage pvr 250 remote not working in 9.10"
date: 2010-01-02
forum: Mythbuntu
---

### Post by splashd on 2010-01-02
I reinstalled Mythbuntu 9.10 on my frontend. All is well, except I cannot get my dogbone Hauppage remote working. LIRC is running and dmesg says the remote control is registered.
Which remote should I be choosing out of Mythbuntu Control Center?
Any other ideas for troubleshooting?
thanks,
Splash

---

### Post by ozite on 2010-01-02
Try
```
sudo modprobe lirc_i2c
```

LIRC seemed to work for me when I put that line into my startup.

---

### Post by diskmaster23 on 2010-01-30
that didn't fix mine. I am having the same problems.

---

