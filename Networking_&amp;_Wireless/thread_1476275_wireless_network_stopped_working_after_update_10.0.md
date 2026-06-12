---
title: "wireless network stopped working after update 10.04"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by diddyone on 2010-05-07
i have lucid installed on my toshiba laptop after after an update my wireless stopped working keep asking for password and my wireless card is not detecting no wifi :

*-network UNCLAIMED     
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: memory:d8000000-d800ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:10:d5:04
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.9 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:4000(size=256) memory:da000000-da000fff memory:d4000000-d401ffff(prefetchable)

please help

---

### Post by chili555 on 2010-05-08
> *-network UNCLAIMED This usually means no driver has claimed your wireless device. I think the device works with the module *ath5k*. Let's load it and see if your device comes to life:```
sudo modprobe ath5k
iwconfig
```Was a wireless interface created? If so, let's make sure it gets loaded on boot:```
sudo su
echo ath5k >> /etc/modules
exit
```If not, let's see what the kernel has to report:```
dmesg | grep -i ath
```Thanks.

---

### Post by diddyone on 2010-05-08
thank you will let you know

---

### Post by solobluejay on 2010-05-08
After switching from 9.10 to 10.04 lost wireless could see SSID and after putting in correct key would still fail to connect. after playing around found that if using WPA/WPA2-personal security mode had to have the encrpytion on my router set to AES only and connected no problem.

Might be worth a trying different security settings on your router just to prove hardware is ok

---

### Post by Shompol on 2010-07-28
> **solobluejay said:**
> if using WPA/WPA2-personal security mode had to have the encrpytion on my router set to AES only and connected no problem

Awesome!  10.04 wireless was working, but after an update BOTH my computers could not connect!
Easiest fix.  Many thanks

---

