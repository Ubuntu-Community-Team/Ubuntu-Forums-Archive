---
title: "ubuntu wireless issues"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by mpolzin2011 on 2010-10-31
i know everyone here has prolly seen this posted numerous times, but i thought this would get quicker results than looking through the threads. i feel like ive done everything. can someone show me the way?

i just recently installed ubuntu and i have issues getting the wireless drivers to work. 

when i plug in an ethernet cable, the internet works just fine.

i need wireless though

when i go into System > admin > hardware drivers
it loads up and has two gray dot drivers. (gray dot meaning this driver is not activated.)

the two drivers listed are 

Broadcom b43 wireless driver
Broadcom STA wireless driver

when i click on either one of them, and hit activate, a box pops up saying "downloading and installing driver..." 
--- then an error message comes up saying "Failed to fetch cdrom:[Ubuntu 10.04.1 LTS_Lucid lynx_-release amd64 (20100816.1)]/pool/main/p/patch/patch_2.6-2ubuntu1_amd64.deb fire not found"

i have also read some posts about Installing "ndisgtk"

so i went into the software center under applications. typed it into the search bar and up comes a "windows wireless driver"

so i chose to install that, and then pops up a box saying

"Please insert the above CD/DVD into the drive"

i installed ubuntu from linux.com so i dont have a cd.



ALSO

--- i have gone into the terminal many times and entered commands like 

sudo iwlist scanning -- interface doesnt support scanning. network is down.
sudo lshw -c network -- and up came this (listed below)


*-network UNCLAIMED 
description: Network controller
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress cap_list
configuration: latency=0
resources: memory:9e200000-9e203fff
*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 02
serial: 00:1e:68:ec:af:8c
size: 100MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=100MB/s
resources: irq:32 ioport:6000(size=256) memory:94010000-94010fff(prefetchable) memory:94000000-9400ffff(prefetchable) memory:94020000-9402ffff(prefetchable)



i feel like ive done everything possible and this damn wireless isnt working. can anyone help me out here?

---

### Post by mpolzin2011 on 2010-10-31
note: also, i forgot to add. when i go into the synaptic package manager and type in ndisgtk and try to install it, an error message pops up saying "unable to lock download directory"

---

### Post by mpolzin2011 on 2010-10-31
bump. can anyone help?

---

### Post by chili555 on 2010-10-31
It usually says it can't lock the directory when you have Synaptic or Update Manager sitting open. Close them.

Re-open Synaptic and look for b43-fwcutter and install it. After it downloads and installs and whirrs and grinds, detach the ethernet cable and reboot. Your wireless should be working.

While you are in Synaptic, go to Settings > Repositories and select Other Software. Uncheck the CDROM so it won't try to use a CD that you don't have.

---

### Post by mpolzin2011 on 2010-11-01
i went to synaptic package manager and attempted to turn off the cdrom you were talking about, nothing said cdrom, it just had two websites in there that i unchecked. and then tried to install what you told me, and its still telling me to insert a cd... im so confused. i just want this all working. any onther ideas?

thanks,
matt

---

