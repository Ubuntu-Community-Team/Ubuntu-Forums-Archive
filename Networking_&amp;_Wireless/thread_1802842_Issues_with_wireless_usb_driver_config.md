---
title: "Issues with wireless usb driver config"
date: 2011-07-12
forum: Networking &amp; Wireless
---

### Post by chamber on 2011-07-12
Having difficulties configuring a driver for an Edimax wireless usb 

[http://www.edimax.com/en/support_detail.php?pd_id=347&pl1_id=1&pl2_id=44](http://www.edimax.com/en/support_detail.php?pd_id=347&pl1_id=1&pl2_id=44)

I have downloaded the driver, and after *make clean* I am running into problems.

When I enter *make* I get the following.

```
make ARCH=i386 CROSS_COMPILE= -C /lib/modules/2.6.32-5-686/build M=/home/conor/rtl8192CU_linux_v2.0.939.20100726  modules
make: *** /lib/modules/2.6.32-5-686/build: No such file or directory.  Stop.
make: *** [modules] Error 2

```

This worked ok on my Ubuntu 10.04 install on my desktop but it does not seems to be working on my Crunchbang 10 latest release on my laptop.

Would anyone have any thoughts?

---

### Post by chamber on 2011-07-14
Bumpety

---

### Post by chamber on 2011-07-18
Bumpety bumpety.

---

### Post by chamber on 2011-07-21
Last bumpety.  Not as urgent anymore, but would ne still nice to hear peoples thoughts.

---

### Post by chili555 on 2011-07-21
I have no idea about Crunchbang 10, but in Ubuntu, you'd need to install *build-essential* and *linux-headers-generic*. I suggest you look in your package manager for similar packages to install and try again.

---

