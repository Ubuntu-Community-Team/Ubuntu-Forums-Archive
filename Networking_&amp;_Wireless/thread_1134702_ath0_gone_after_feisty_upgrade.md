---
title: "ath0 gone after feisty upgrade"
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by john_d on 2009-04-23
upgraded to jaunty on line today toshiba laptop.. no ath0 after ifconfig.. had to run knetwork manager manually but still no ath0.. how can i get wireless back up?

---

### Post by t0mppa on 2009-04-23
Ath0 is missing or just not working?

Run ```
lshw -C network
``` and let's see what it says.

---

### Post by greenrubberducky on 2009-04-26
Okay...I see the original poster isn't going to respond. I will, though.
Let's say I don't see ath0 in the ifconfig output, but I do see this when I run lshw:
```
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: aa:29:5a:74:04:1b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

I had it running on 8.10 with the madwifi drivers, now it doesn't work after the upgrade. Using the built-in madwifi proprietary drivers.

---

### Post by t0mppa on 2009-04-27
Unclaimed means that no drivers are associated with the interface. Folks at madwifi swore the ath5k in 9.04 would make the older madwifi drivers obsolete. And for me (AR242x chip), the upgrade to Jaunty worked out of the box, with ath5k taking over the wireless. So, did you just straight away go and pick the proprietary driver or did the ath5k not work for you?

---

