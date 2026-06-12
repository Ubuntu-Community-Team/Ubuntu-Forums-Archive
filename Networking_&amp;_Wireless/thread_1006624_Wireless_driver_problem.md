---
title: "Wireless driver problem"
date: 2008-12-09
forum: Networking &amp; Wireless
---

### Post by markomk on 2008-12-09
I fixed a lot of problems here :) i hope i can fix to.

when i try command sudo airmon-ng this shows:
-------------------------------------------------

Interface Chipset Driver

eth1 UNKNOWN wl
--------------------------------------------------
a little info:
*-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:6e:66:66
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl wireless=IEEE 802.11bg


02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g


how can i fix?

---

### Post by gnusci on 2008-12-09
Please, I recommend you to read this sticky:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

And this post:

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Ayuthia on 2008-12-09
I don't think that the wl driver is supported by airmon-ng at this time.  This is the new Broadcom driver that was just released in July.

---

### Post by markomk on 2008-12-09
> **gnusci said:**
> Please, I recommend you to read this sticky:

[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

And this post:

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)


the firstone didn't help :S i'll try with second

---

### Post by Ayuthia on 2008-12-09
Is your wireless working or are you tyring to use airmon-ng?  If it is not working, please post the results of lshw -C network and sudo iwlist scan.

---

