---
title: "Need help with ralink rt2570, keep getting modprobe error"
date: 2009-07-04
forum: Networking &amp; Wireless
---

### Post by ptindall on 2009-07-04
I need help installing the aircrack-ng drivers for a Linksys WUSBG54 v4 with rt2570 driver. I am running Ubuntu 9.04 

I have compiled and installed but I keep getting a error when I try to modprobe.  I've looked everywhere and haven't been able to find a solution.  Can anyone help me?

Steps I've taken:

wget [http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt2570-k2wrlz-1.6.3.tar.bz2](http://homepages.tu-darmstadt.de/~p_larbig/wlan/rt2570-k2wrlz-1.6.3.tar.bz2)
tar -xvjf rt2570-k2wrlz-1.6.3.tar.bz2
cd rt2570-k2wrlz-1.6.3/Module
make && make install
modprobe rt2570

I am using root access for all of this.

When I try to modprobe, it always comes back with this:

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ralink, it will be ignored in a future release.
FATAL: Module rt2750 not found.

Please help.

---

### Post by ptindall on 2009-07-04
Sorry, I forgot to add that I have also blacklisted the following drivers:

blacklist rt2500usb
blacklist rt2x00lib
blacklist rt73usb 

I have been trying to get this to work for several weeks now with no luck whatsoever.  Any help would be greatly appreciated.

---

