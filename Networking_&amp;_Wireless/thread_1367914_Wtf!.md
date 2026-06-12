---
title: "Wtf?!?"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by james1991 on 2009-12-30
ok what does this mean-
i ran the "lshw -c network" line and this came up
*-network UNCLAIMED
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c2000000-c200ffff
Every where i look no one explains what it means when it says "UNCLAIMED" 
whats it mean?

---

### Post by puppywhacker on 2009-12-30
That means that a network interface is present, but there is no driver module loaded for it that took control over it.

It is an atheros 5000 for which the module is ath5k. you can load it with modprobe and with depmod it will load the module at startup.

```
modprobe ath5k
depmod -a
```

you can see the kernel messages with "dmesg" or in the logfile "/var/log/messages"

---

