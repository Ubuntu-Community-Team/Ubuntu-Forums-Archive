---
title: "Wireless USB adapter stopped working overnight?"
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by Nate Hofmann on 2013-06-28
I have a Trendnet tew-6646usb v2.0 wireless usb adapter that is not picked up by ubuntu today even though it was yesterday. Help?

---

### Post by chili555 on 2013-06-28
Does it start working if you just reload the driver?```
sudo modprobe 8192du
```Is there any error with modprobe?

---

### Post by Nate Hofmann on 2013-06-28
It says the Module 8192du is not found.

---

### Post by chili555 on 2013-06-28
I suspect there was an updated kernel version. When this happens, you will need to re-compile for the newer kernel, also known as linux-image:```
cd rtl8192du
make clean
make
sudo make install
sudo modprobe 8192du
```Is it working now?

---

### Post by Nate Hofmann on 2013-06-28
Thank you, fixed it again!

---

