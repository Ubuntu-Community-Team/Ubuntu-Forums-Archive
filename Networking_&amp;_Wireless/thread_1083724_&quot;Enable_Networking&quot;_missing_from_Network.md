---
title: "&quot;Enable Networking&quot; missing from NetworkManager"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by Kay Fisher on 2009-03-01
I'm new to ubuntu so please go slow.  When I boot the live CD the NetworkManager 0.7.0 has both Enable Networking and Enable Wireless boxes checked.

After an install I tried many ways to get by broadcom builtin wireless configured correctly and somewhere along the way the "Enable Wireless" selection went away.  I followed all the directions in this forum titled "How to install native broadcom drivers for BCM4311, BCM4312, BCM4321, and BCM4322".  I think my "Enable Wireless" option went away before I did all that.
Anyway I was successful at creating a wl.ko driver and think I put it in right.  I suspect if I could just figure out how to get the NetworkManager to wake up it might work.

Since I only connect wirelessly thru a hot spot I have to reboot into Windows XP to look for the next thing to try to solve this problem.

Thanks in advance for any help.

Respectfully,
Kay R. Fisher

---

### Post by smani on 2009-03-01
Look at the output of
```
sudo lshw
```
Search for your wireless card, does it say UNCLAIMED? If so, the module is not loaded: try
```
sudo modprobe module_name
```
If that worked, then the problem probably is that the module is not automatically loaded at startup, in which case you have to add module_name to /etc/modules.

---

### Post by Kay Fisher on 2009-03-01
Tried that - no help.
1St the title should have been "Enable Wireless" missing from NetworkManager.  After I posted I tried to change it but couldn't figure out how to change a title.  If someone else can change it please do.

The output of sudo lshw was:

           *-network:0 UNCLAIMED
                description: Network controller
                product: BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Transceiver
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:06:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: latency=64

So I tried typing in sudo modprobe wl
didn't seem to have any effect.

The contents of my etc/modules is:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
sbp2
ieee80211_crypt_tkip

wl
k

Any help appreciated.
Respectfully,
Kay R. Fisher

---

