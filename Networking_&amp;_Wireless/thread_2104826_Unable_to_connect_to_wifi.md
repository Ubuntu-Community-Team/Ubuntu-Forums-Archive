---
title: "Unable to connect to wifi"
date: 2013-01-14
forum: Networking &amp; Wireless
---

### Post by Mariius on 2013-01-14
I installed ubuntu 12.10 32bit on my msi fx600 laptop, which has intel wifi link 1000 bgn wireless card. I am not able to connect to any wifi. Ubuntu is able to find wifi networks around me, but I am not able to connect to any of them.
What should I do? Could you please be specific, because I have never used any linux distro and this is very confusing for me.

---

### Post by praseodym on 2013-01-14
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk
lsmod
iwconfig
route -n
rfkill list
```

---

