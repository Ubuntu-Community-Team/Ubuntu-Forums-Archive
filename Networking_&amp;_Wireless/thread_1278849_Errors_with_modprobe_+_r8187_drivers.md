---
title: "Errors with modprobe + r8187 drivers"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by JayUK20 on 2009-09-30
I just built the patched version on the rtl8187 drivers but I am having problems loading it as when I type sudo modprobe r8187 I get the following warnings:

WARNING: all config files need .conf /etc/modprobe.d/vmware-tools it will be ignored in a future release

WARNING: all config files need .conf /etc/modprobe.d/blacklist it will be ignored in a future release

How or what do I need to do?

---

### Post by chili555 on 2009-09-30
> How or what do I need to do?Nothing. The title of your post says 'errors' however, you have warnings and not errors. Moreover, there is no mention of being unable to load r8187 for any reason. You can check to see if it's loaded with:```
lsmod | grep 8187
```There is considerable comment on the internet about 'WARNING: all config files need .conf.' Some say to ignore it and some say to fix it. I suggest you Google it and decide for yourself. If you think you want to fix it, do:```
sudo mv /etc/modprobe.d/vmware-tools /etc/modprobe.d/vmware-tools.conf
sudo mv /etc/modprobe.d/blacklist /etc/modprobe.d/blacklist.conf
```DISCLAIMER: I am not recommending that you do so or not. You decide.

---

