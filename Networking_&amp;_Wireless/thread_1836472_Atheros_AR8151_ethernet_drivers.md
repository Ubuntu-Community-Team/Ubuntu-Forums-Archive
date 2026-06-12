---
title: "Atheros AR8151 ethernet drivers"
date: 2011-08-31
forum: Networking &amp; Wireless
---

### Post by busav on 2011-08-31
Hi !

I have one big problem ... i can't install the atheros driver on my machine! I try everything, every idea on every post and i mean EVERYTHING ! On make install command we have some errors and the module atl1 not found !!!

...

---

### Post by praseodym on 2011-08-31
Hi,

please show:

```
uname -a
lspci -nnk | grep -iA2 net
lsmod
cat /var/lib/NetworkManager/NetworkManager.state
```
Did you install the kernel-headers and compiling tools before?

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
```

---

### Post by tim273 on 2012-02-17
[http://ubuntuforums.org/showthread.php?t=1677122](http://ubuntuforums.org/showthread.php?t=1677122)

---

