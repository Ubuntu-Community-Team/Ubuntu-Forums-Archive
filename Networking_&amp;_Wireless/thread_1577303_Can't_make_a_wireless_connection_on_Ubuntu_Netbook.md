---
title: "Can't make a wireless connection on Ubuntu Netbook Edition 10.04"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by clandestinerogue on 2010-09-18
This is my first time using Ubuntu, and I can't seem to find a way to connect to the internet wirelessly. I can't even find the "Network Manager" and can't see any wireless network available.
 
I'm using Ubuntu Netbook Edition 10.04. I dual boot with Windows 7 and the wireless connection works properly on Windows.
 
Here's my lshw -C network output:
```
 
PCI (sysfs) 
*-network 
description: Ethernet interface
product: Atheros AR8132 / L1c Gigabit Ethernet Adapter
vendor: Atheros Communications
physical id: 0
bus info: pci@0000:01:00.0
logical name: eth0
version: c0
serial: 70:5a:b6:f8:62:ef
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
resources: irq:28 memory:57000000-5703ffff ioport:5000(size=128)
*-network UNCLAIMED
description: Network controller
product: Broadcom Corporation
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: latency=0
resources: memory:56000000-56003fff

```
 
 
and iwconfig output:
```
 
lo   no wireless extensions.
 
eth0 no wireless extensions.

``` 
 
I have completely no idea what those mean... :(

---

### Post by cpgos on 2010-09-19
I am having similar problems, see my post "Wireless broadband modem" 

There is help at the post called "please read if you need to configure a 3g modem on 10.04" but unfortunately this did not work for me.

Best regards,
cpgos

---

### Post by clandestinerogue on 2010-09-22
whoa! it's working now! =) not sure what i did to solve the problem. i guess i just went to system > administration > hardware drivers, and let it do its job (you'll need a temporary internet connection btw). you should try that too, cpgos (if you haven't)!

---

