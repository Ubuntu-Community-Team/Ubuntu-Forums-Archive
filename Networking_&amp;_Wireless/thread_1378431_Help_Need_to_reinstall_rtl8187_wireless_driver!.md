---
title: "Help: Need to reinstall rtl8187 wireless driver!"
date: 2010-01-11
forum: Networking &amp; Wireless
---

### Post by bedhead75 on 2010-01-11
I've seemed to have lost the original rtl8187 wireless driver in Ubuntu 9.10 after trying to install the "latest" drivers provided by me from Realtek.  To install the latest drivers, I had to run "make", "make install", and then "reboot".  But there were issues with network manager not "seeing" my wireless USB adapter afterwards and I couldn't get wireless working.  I then ran "make uninstall", and "make clean" to remove those new drivers, but the original drivers seem to now be missing and I can't load them anymore.  I get "FATAL: Module rtl8187 not found" when I run "modprobe rtl8187", which worked fine before all of this.  How do I get them back?

---

### Post by changingstate on 2010-01-11
This looks like a damaged kernel installation. Repair with :

sudo apt-get --reinstall <name of kernel package>

You can discover the name of your kernel package by searching for linux-image in synaptic.

---

### Post by bedhead75 on 2010-01-11
Thanks a bunch!  That fixed it.

---

