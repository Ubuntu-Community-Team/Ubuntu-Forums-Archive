---
title: "Sketchy Internet  with Ubuntu"
date: 2011-05-14
forum: Networking &amp; Wireless
---

### Post by JohnWentzville on 2011-05-14
I recently installed Ubuntu 10.10 on my Toshiba A215, and ever since, the wireless connection has been very inconsistent.  After a while of it working, I will suddenly be kicked off the internet, and the only way to get back on is to unplug the machine and take out the battery (when the battery is working), and then power it up again.  When it decides not to work, it will repeatedly ask me for an access code, then eventually stops.  Help please?

---

### Post by pSYcl0Ne on 2011-05-14
I was having similar problems after a fresh install. turns out I needed to add some newer wifi drivers to the blcklist

/etc/modprobe.d/blacklist-rt2800.conf


# This is to fix wifi on the MSI Wind with the Ralink RT2700E.
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib

obviously your drivers will be different, but hopefully this points you in the right direction

---

