---
title: "Wifi woes (madwifi-ng)"
date: 2006-05-10
forum: Networking &amp; Wireless
---

### Post by malegria on 2006-05-10
I've recently installed madwifi from CVS, mainly to fix the fact that my signal would keep dropping with the linux-restricted-modules package. But now my internet connection won't start-up at boot. I have to manually go into "Networking" and start it up.

Here's my /etc/network/interfaces```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#auto eth0

#iface ath0 inet dhcp
iface ath0 inet dhcp
wireless-essid cervantes

auto ath0

```

Here is my /etc/modules:```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod
fglrx
fuse

ath_pci
ath_hal
if_athrate
if_ath_ahb


```

Any ideas?

---

### Post by jml on 2006-05-10
Config files are not my strong suit, but one idea comes to mind.  In your /etc/network/interfaces file; try this change.

#iface ath0 inet dhcp
**auto ath0**
iface ath0 inet dhcp
wireless-essid cervantes


Hope it helps.

Joe

---

### Post by malegria on 2006-05-10
Will try.

-------

Didn't work.

---

