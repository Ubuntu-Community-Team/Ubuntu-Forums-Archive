---
title: "Wireless is greyed out........"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by optimistique1 on 2009-06-10
Hi All, I just reinstalled Ubuntu 9.04 and for some reason I have no wireless now where as before it was fine.  When I click on the network Icon the wireless is greyed out........

My wireless card is Atheros, but like I said before it was working fine a few hours ago with no tweaks or hacks needed..

The Laptop is HP G-60 which does have a wireless on/off button but this doesn't work with linux anyway, it only lights up blue with Windows installed.

Has anyone any ideas how to fix this please?

Many thanks

Garry

---

### Post by superprash2003 on 2009-06-10
the wireless switch does have an effect on wireless functionality.. post output of **lshw -C network**

---

### Post by yaroto98 on 2009-06-10
my wireless switch always worked in ubuntu, hit it a few times to make sure. then go into the network manager and make sure it's enabled.

---

### Post by optimistique1 on 2009-06-10
Hi Buddy here's the readout - 

garry@garrywestwell:~$ lshw -c network 
WARNING: you should run this program as super-user. 
  *-network                
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1f:16:67:50:04 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes 
  *-network 
       description: Wireless interface 
       product: AR242x 802.11abg Wireless PCI Express Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: wmaster0 
       version: 01 
       serial: 00:24:2b:18:4a:e7 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list logical ethernet physical wireless 
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg 
  *-network DISABLED 
       description: Ethernet interface 
       physical id: 2 
       logical name: pan0 
       serial: 86:c9:9e:65:2c:a2 
       capabilities: ethernet physical 
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes 
garry@garrywestwell:~$

---

### Post by optimistique1 on 2009-06-10
Anyone any ideas that may help me with this please?

---

### Post by bkratz on 2009-06-10
There are a lot of threads regarding this device---here is  one example.

[http://ubuntuforums.org/showthread.php?t=987955&highlight=ath5k_pci](http://ubuntuforums.org/showthread.php?t=987955&highlight=ath5k_pci)

---

### Post by optimistique1 on 2009-06-10
Hi All, according to the terminal read out, the Atheros drivers are loaded but the network is disabled.  How to I re-enable it?

description: Wireless interface 
product: AR242x 802.11abg Wireless PCI Express Adapter 
vendor: Atheros Communications Inc. 
physical id: 0 
bus info: pci@0000:02:00.0 
logical name: wmaster0 
version: 01 
serial: 00:24:2b:18:4a:e7 
width: 64 bits 
clock: 33MHz 
capabilities: bus_master cap_list logical ethernet physical wireless 
configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg 
*-network DISABLED 
description: Ethernet interface 
physical id: 2 
logical name: pan0 
serial: 86:c9:9e:65:2c:a2 
capabilities: ethernet physical 
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by superprash2003 on 2009-06-11
post output of
1)sudo iwlist scanning
2)iwconfig

---

