---
title: "Lenovo Y580 - Ethernet Interface : Device not found."
date: 2013-07-06
forum: Networking &amp; Wireless
---

### Post by ad17yam on 2013-07-06
Hi Guys, 

I am facing a problem getting my ethernet working on Ubuntu 12.04.2 LTS \n \l, running on Lenovo Y580. It works on my windows partition. "ifconfig" shows 'lo' and 'wlan0' but no ethernet.
The output for "sudo lshw -C network" is :
  
*-network UNCLAIMED     
       description: Ethernet controller
       product: AR8161 Gigabit Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 08
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:d3600000-d363ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: c4
       serial: XX:XX:XX:XX:XX:XX
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-23-generic firmware=18.168.6.1 ip=192.168.2.32 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:45 memory:d3500000-d3501fff


I am bit new at this. Any help/guidance/redirection, would be greatly appreciated.

Thanks, 
Aditya.

---

### Post by chili555 on 2013-07-06
Tell us more about your ethernet device:```
lspci -nn -d 1969:
```Also tell us if you'd install Ubuntu 13.04 to get the ethernet to work immediately.

---

### Post by ad17yam on 2013-07-06
lspci -nn -d 1969: gives me the following
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8161 Gigabit Ethernet [1969:1091] (rev 08)
I would be willing to upgrade to a 13.04, if that doesnt involve me rebooting my system, if there is a simple way to upgrade the kernel, that
would be awesome.

---

### Post by ad17yam on 2013-07-06
Hey chili555, 

Thanks a lot man, I was able to solve the issue by a simple update via the update manager. Wasn't such a huge issue after all, although I did spend one night trying to find the right drivers....

:P

---

