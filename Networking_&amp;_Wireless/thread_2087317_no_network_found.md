---
title: "no network found"
date: 2012-11-23
forum: Networking &amp; Wireless
---

### Post by baronn on 2012-11-23
Hello, I just re-installed ubuntu after a format, but I had an old version (10.smth). Even though the router is working properly, I don't have internet access from ubuntu. 

The PC is connected via an ethernet cable, and windows is working properly. Any ideas?

---

### Post by 2F4U on 2012-11-23
Can you provide the output of

ifconfig -a
lspci

to see what hardware you have and if the system detects your hardware. However, it may be easier to install a newer version of Ubuntu, either 12.04 or 12.10, because depending on what version you currently have, upgrading may be quite some effort.

---

