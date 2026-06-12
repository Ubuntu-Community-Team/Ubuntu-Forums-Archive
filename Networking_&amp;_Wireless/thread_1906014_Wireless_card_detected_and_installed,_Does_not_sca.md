---
title: "Wireless card detected and installed, Does not scan."
date: 2012-01-08
forum: Networking &amp; Wireless
---

### Post by MrMichaelHill on 2012-01-08
After a short time moving house I've got my system back up and running, Installed Ubuntu 11.10 64bit and my computer now runs a RaLink wireless card I think a 3062 model, It's detected I have it but does not scan :(

When I use iwlist scan it says my ethernet ports do not support it *obviously* and that wlan0 - No Scan Results...
:(

Thanks in advance!

---

### Post by MrMichaelHill on 2012-01-09
Oh and I can't really get the system connected using wired, the router is downstairs in my house :(

---

### Post by varunendra on 2012-01-12
Hi,

To confirm the model & driver in use, and some other details, please post outputs of:
```
uname -rm
sudo lshw -C network
ifconfig -a
iwconfig
lsmod
rfkill list all
cat /etc/network/interfaces
```

And... are you sure you are in the range of available networks and the signals are strong enough?

---

