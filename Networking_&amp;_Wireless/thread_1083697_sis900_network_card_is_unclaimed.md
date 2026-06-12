---
title: "sis900 network card is unclaimed"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by zulixp on 2009-03-01
Hey everyone, this forum is my last chance to fix a problem, that 4 days are killing my nerb cells.
Network card sis900 suddenly became a unclaimed. an under windows card is working.

there is a report from sudo lshw -c network
```
*-network UNCLAIMED     
       description: Ethernet controller
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 7
       bus info: pci@0000:03:07.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=11 mingnt=52
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:29:27:58:75:d1
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

I've also tried these commands:
```
sudo /etc/init.d/udev restart
sudo modprobe -r sis900
sudo modprobe sis900
sudo /etc/init.d/networking restart
```
but nothing. terminal shows, the device not found

---

### Post by zulixp on 2009-03-01
About a hour ago I've solved this problem:
I've used a tool, which installs Windows Wireless drivers (which can be found on synaptic package manager) And I've forced a Windows driver. and after sudo modprobe sis900, my network is working.

Sorry for my bad English.

---

