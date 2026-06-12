---
title: "tp-link tl-wn851n - no wireless connection"
date: 2010-11-28
forum: Networking &amp; Wireless
---

### Post by howiebinnz on 2010-11-28
i have tried to get the above wireless card working - mostly with the easy madwifi script in these forums - all to no avail. i have seen a couple of posts where people have said they have got this card working, so i must have done something to screw things up. here is some output:
```
   	 	 	 	p { margin-bottom: 0.21cm; }  lspci | grep Atheros 
 01:07.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01) 
 Codename: maverick
 uname -r    2.6.35-23-generic 
 

 sudo lshw -C network 
   *-network:0 UNCLAIMED    
        description: Network controller 
        product: AR922X Wireless Network Adapter 
        vendor: Atheros Communications Inc. 
        physical id: 7 
        bus info: pci@0000:01:07.0 
        version: 01 
        width: 32 bits 
        clock: 66MHz 
        capabilities: pm bus_master cap_list 
        configuration: latency=32 
        resources: memory:e7000000-e700ffff 
    
 lsmod | grep ath 
 ath_pci               179564  0  
 wlan                  220184  1 ath_pci 
 ath_hal               396940  1 ath_pci 
 

 sudo ./madwifi.sh --info 
 Found at least one Atheros device. 
 Linux howard-desktop 2.6.35-23-generic #40-Ubuntu SMP Wed Nov 17 22:15:35 UTC 2010 i686 GNU/Linux 
 Distro: Debian 
 01:07.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01) 
 	Subsystem: Atheros Communications Inc. Device 2091 
 	Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 5 
 	Memory at e7000000 (32-bit, non-prefetchable) [size=64K] 
 	Kernel modules: ath9k 
  
 ath_pci               179564  0  
 wlan                  220184  1 ath_pci 
 ath_hal               396940  1 ath_pci 
 wifi0: 0 ath0: 0 
 
```

i am a bit of a nooby at all this wireless stuff, help would be much appreciated - happy to post any further output required.
thnx

---

### Post by howiebinnz on 2010-11-30
well, solved as far as getting wifi up - had purchased a new modem/router plus a new 2tb hard drive. decided easiest thing was to back up all my data and do a fresh install (was originally ubuntu 9 something with upgrades along the way). after re-install found the wireless network without a problem, ended well anyway!!:D:P

---

