---
title: "Broadcom BCM 4311 not able to connect to any wireless"
date: 2009-09-05
forum: Networking &amp; Wireless
---

### Post by pilot26 on 2009-09-05
I an new to ubuntu and my wireless was working until about a week ago. I have looked around and have tried many options that looked that they fit my situation, but to no avail. 

when I look under hardware driver I find  Broadcom STA and B43 driver I have tried to install both at different times but no change.

when I run lshw -C network I get 

 *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:ba:02:e7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A ip=192.168.1.100 latency=0 module=sky2 multicast=yes
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1a:01:35:bf:18:97
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  

I have tried the ndiswrapper but I cant find any drivers.

so I dont know what else to do 

thanks
Matt

---

### Post by pilot26 on 2009-09-05
BUMP..

any and all suggestions are welcome. I'm just so lost and in need of some leads.

thanks
Matt

---

### Post by pilot26 on 2009-09-06
bump.

---

### Post by uylug on 2009-09-06
> **pilot26 said:**
> bump.

what happens if you run these:

```
sudo ifconfig wlan0 up
```
```

sudo iwlist scan
```

---

### Post by colinireland on 2009-09-06
Have you tried editing /etc/NetworkManager/nm-system-settings.conf

from this:
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=**[COLOR="Red"]false[/COLOR]**

to this
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=**[COLOR="Red"]true[/COLOR]**

---

### Post by pilot26 on 2009-09-06
sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

vboxnet0  Interface doesn't support scanning.

pan0      Interface doesn't support scanning


I hope that this helps solve the problem

Matt

---

### Post by pilot26 on 2009-09-06
When I try to open Have you tried editing /etc/NetworkManager/nm-system-settings.conf I get this error.

nm-system-settings.conf" cannot be opened

so what did I do wrong during setup?

thanks
Matt

---

### Post by colinireland on 2009-09-07
did you try sudo gedit /etc/NetworkManager/nm-system-settings.conf ?

---

### Post by colinireland on 2009-09-07
hey just read your previous post. Sounds like you need to reinstall the drivers. I have a bcm4312. This post helped out alot.

[http://ubuntuforums.org/showthread.php?t=896713]("http://ubuntuforums.org/showthread.php?t=896713")

---

