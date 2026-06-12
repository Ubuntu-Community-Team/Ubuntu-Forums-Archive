---
title: "Wireless&amp;Wired problem, Atheros AR242x802.11abg, Ubuntu8.10,Esprimo V5535"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by 80aless on 2009-01-21
Hi, 
I am in the depression phase because my wireless (and wired network) has not been working for months. Please, please, please help! 
I will do something for you if I can, or I send some money to your favorite non-profit organization or political party if you like ( if you do not like this, do not take it seriously).
Thanks,Alex

Following the rules in the sticky:
Laptop: see title
Atheros: see title
Ubuntu: see title
I have ath_pci, sis190, ath5k, ath_hal blacklisted in /etc/modprobe.d/blacklist
I had ndiswrapper I think, then I tried madwifi , I just did make uninstall to uninstall madwifi but I do not know if it worked.
```

modprobe -l | grep ath
/lib/modules/2.6.27-7-generic/net/ath_pci.ko
/lib/modules/2.6.27-7-generic/net/ath_rate_onoe.ko
/lib/modules/2.6.27-7-generic/net/ath_rate_sample.ko
/lib/modules/2.6.27-7-generic/net/ath_rate_amrr.ko
/lib/modules/2.6.27-7-generic/net/ath_rate_minstrel.ko
/lib/modules/2.6.27-7-generic/net/ath_hal.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/net/wireless/ath9k/ath9k.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/md/dm-multipath.ko
/lib/modules/2.6.27-7-generic/kernel/drivers/md/multipath.ko
```


```




iwconfig
  lo no extension
ipconfig
  bash: ipconfig: command not found

lsmod | grep "wlan_module_name"
  #nothing
dmesg
   #too long to write it down, ask me if you really need it
sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0

iwlist scan
   lo   interface does not support scanning
uname -mr
   2.6.27-7-generic i686


sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          eth0: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
wlan1: ERROR while getting interface flags: No such device
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFADDR: No such device
wlan1: ERROR while getting interface flags: No such device
wlan1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan1.

```

---

### Post by 80aless on 2009-01-26
never mind, the people of linuxforums.com helped me.
The problem was that I had build-essential but not the right linux-source and linux-headers. then install 
[http://linuxwireless.org/en/users/Download]("http://linuxwireless.org/en/users/Download")

---

