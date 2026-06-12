---
title: "Jaunty, Atheros and Kismet"
date: 2009-05-26
forum: Networking &amp; Wireless
---

### Post by oaxacamatt1 on 2009-05-26
Hi All, I am trying to get Kismet up and going. 

1) I was able to install and get Madwifi for my Atheros driver up and going. 
<<part of sudo lshw -C Network>>
*-network
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:d2:2b:ad:e6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

2) I 'think' I set up the config file for Kismet OK.
<<part of config file>>
source=ath5k,wmaster0,Atheros

3) But when I run <sudo Kismet> I get:
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unable to find default channel set IEEE80211b or specific channel sets for source Atheros
Done.

Cheers for any help,

---

### Post by chili555 on 2009-05-26
> source=ath5k,[COLOR="Red"]wmaster0[/COLOR],AtherosI think you want wlan0. Please amend your kismet.conf and let us know.

---

### Post by oaxacamatt1 on 2009-05-26
Dam, that did it.
Thanks

---

### Post by maciasoo on 2009-08-05
Great one! I lost 2 hours to find a solution but that's the perfect one! :D

---

### Post by MrSandman on 2009-12-01
source=ath5k,wlan0,Atheros 

Beautiful!!

---

