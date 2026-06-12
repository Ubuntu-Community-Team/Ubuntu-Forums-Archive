---
title: "Connect to my wireless network, save my marraige!"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by vcell on 2010-08-03
My wireless network is running just fine. I'm connected on one of the laptops (Ubuntu 10.04) and on the Mac Mini. However, I just upgraded my wife's Dell Inspiron from Ubuntu Desktop 8.04 to 10.04. Now the Network Manager is not pointing to ANY networks.

On my one laptop (and on my Mac Mini) I'm showing four networks in the area, including mine. But on the Inspiron, nada.

Seeing as how my wife only uses her laptop for internet access, and it was working fine when 8.04,to suddenly not have it is not an option. You gotta help! What happened?

If it helps, my connection comes in broadband, and goes wireless via Apple AirPort. What else do you need to know?

---

### Post by vcell on 2010-08-04
More information.

On my laptop that has connection I entered:

sudo lshw -C network

and got:


PCI (sysfs)  
  *-network               
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:d8:f0:c1
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.1.6 multicast=yes wireless=IEEE 802.11bg

On the Inspiron without connection the same command returns:


*-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:40:93:8c
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:26:5e:1d:35:68
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

Does this help?

---

### Post by Humanity to others on 2010-08-04
You have to install wireless driver

---

### Post by vcell on 2010-08-04
Outstanding. Could I copy the one from this Dell laptop to USB and copy it to the Inspiron? I'm not sure where to locate the driver on the system. (i know, cuz i sound like i know what i'm doing, but i don't).

---

### Post by Tiberion on 2010-08-04
You will have to connect via ethernet and go to sytem/admin/hardware drivers and enable the restricted drivers for broadcom.  After install you should be good to go with your wireless.  Just make sure you enable wireless by right click network connection in the toolbar

---

### Post by vcell on 2010-08-04
Got it. solved. thanks.

---

### Post by Charly85551 on 2010-08-04
> **vcell said:**
> Got it. solved. thanks. Happy wife):P

---

