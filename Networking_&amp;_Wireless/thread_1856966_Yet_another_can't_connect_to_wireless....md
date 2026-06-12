---
title: "Yet another can't connect to wireless..."
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by jfsain on 2011-10-09
I just installed Ubuntu last night and have thus far not been able to connect to wireless.  No connections are shown.  I've installed ngisdtk, but I need the .inf files and I'm not sure where to get them.  Because every thing I've read has asked the poster for it, here is the dump from sudo lshw -C network:

```


PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: AR8151 v1.0 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:6a:8a:1c:26:8f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:93400000-9343ffff ioport:2000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: BCM43225 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 18:f4:6a:16:6e:a8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=brcm80211 driverversion=2.6.38-8-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:92400000-92403fff


```

---

### Post by praseodym on 2011-10-09
Hi,

uninstall ndiswrapper completely and blacklist the module brcm80211:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
echo "blacklist brcm80211" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo depmod -a
```
Reboot and install the Broadcom-STA-driver vie cable under "additional drivers"

---

