---
title: "Broadcom BCM43224 connection issue."
date: 2011-03-15
forum: Networking &amp; Wireless
---

### Post by Xeameres on 2011-03-15
I am trying to install ubuntu on an HP Pavillion dv7 laptop. The installation worked just fine. However, I cannot connect to our Linksys router wirelessly. (I haven't tried plugging it in directly, but that would be a problem.)
My iwconfig says
> 
lo        no wireless extensions
eth0    no wireless extensions

I'm typing this all from my desktop while staring down at the terminal. 

I have tried searching for "broadcom" in Synaptic, however all that came up was the "bcmwl-modaliases" package, which is already installed.

I typed in "lspci | grep Network" into the terminal, I got
> 
0:200.0 Network controller: Broadcom Corporation BCM43224 802.lla/b/h/n (rev 01)

I would very much appreciate any assistance, as the only problem I'm having with Ubuntu so far is getting it to connect to the internet.

---

### Post by garvinrick4 on 2011-03-15
Run this in a terminal and copy and paste results to your thread will give users your network cards:
```
sudo lshw -C network
```

---

### Post by Xeameres on 2011-03-15
> **garvinrick4 said:**
> Run this in a terminal and copy and paste results to your thread will give users your network cards:
```
sudo lshw -C network
```
*-network UNCLAIMED
description: Network controller
product: BCM43224 802.11a/b/g/n
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
version: 01
width: 64 bits
clock: 33 MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: memory: c3400000-c3403fff

*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co. Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 03
serial: 98:4b:e1:90:5d:e2
size: 10MB/s
capacity: 1GB/s
width: 64 bits
clock: 33MHz

---

### Post by garvinrick4 on 2011-03-16
Check and see if you have these drivers to install in Synaptics and install.
Just type "bcmwl-kernel-source" in search box of Synaptics package manager. without quotes.

---

