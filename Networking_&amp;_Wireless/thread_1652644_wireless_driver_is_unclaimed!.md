---
title: "wireless driver is unclaimed!"
date: 2010-12-25
forum: Networking &amp; Wireless
---

### Post by Nathanielb on 2010-12-25
I downloaded ubuntu on my wireless netbook
my wireless network connection was not working so i checked on terminal and it said it was unclaimed meaning that ubuntu is not recognizing my built in wireless driver (hardware) what should i do becayse ubuntu could also not find the ndiswrapper? please help

---

### Post by dineshs on 2010-12-25
Please post output of```
sudo lshw -C network
```

---

### Post by Nathanielb on 2010-12-25
*- network UNCLAIMED
descriprion: network controller
product: broadcom corporation
vendor: broadcom corporation
physical ID: 0
bus info: pci@0000:02:00.0
version: 01
width: 64 bits
clock: 33 MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: memory: 56000000-56003fff

---

### Post by Nathanielb on 2010-12-25
also above that it said my ethernet was fine

---

### Post by Nathanielb on 2010-12-25
i checked hardware drivers and no drvers were there

---

### Post by dineshs on 2010-12-25
What about ```
lspci
```

---

### Post by Nathanielb on 2010-12-26
Came up with a big list this is what it said for network controller 
02:00.0 Network Controller: Broadcom Corporation Device 4727 (rev 01)

---

### Post by dineshs on 2010-12-27
I am not an expert.I think these links can help
[http://ubuntuforums.org/showthread.php?t=1424280](http://ubuntuforums.org/showthread.php?t=1424280)
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)
Note : You may run ```
lspci -n | grep 14e4
``` and compare the PCI id with the list of devices in the second link.If it matches (I think you will get [14e4:4727] you may install the driver as explained in the first link.Hope your wired connection works OK.
If you are using 10.10 read 
[http://ubuntuforums.org/showthread.php?t=1604868](http://ubuntuforums.org/showthread.php?t=1604868)

---

