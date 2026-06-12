---
title: "lower signal strength under ubuntu than Windows 7"
date: 2013-01-27
forum: Networking &amp; Wireless
---

### Post by pspencil on 2013-01-27
The wifi is really poor under ubuntu 12.10. It can still access internet sometimes, but very slow, much slower than in windows 7. 

Under lspci -vv, it shows that the driver & kernel driver are both rtl8192se which is correct according to my windows device manager. 

Any suggestions?

---

### Post by mujjingun on 2013-02-03
Im having the same problem too! It keeps asking me to type the wpa key again and again. Help!

---

### Post by ahallubuntu on 2013-02-03
> **mujjingun said:**
> Im having the same problem too! It keeps asking me to type the wpa key again and again. Help!

Unless you have exactly the same wireless card, start your own thread, after reporting the output of these terminal commands:

```
sudo lshw -C network
lsusb
lspci

```

so someone can figure out which wireless card you have.  The solution usually depends on the specific hardware you have.

---

