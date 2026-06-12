---
title: "Kismet for Master's Research"
date: 2010-06-14
forum: Networking &amp; Wireless
---

### Post by OOzypal on 2010-06-14
Hello,

I am doing a small research using Kismet. I need help configuring Kismet with my Asus A52J. The Wireless card in my laptop is AR5B95. When I start Kismet I get the following error

```
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'AR5B95' in source 'AR5B95,wlan0,Wifi'
Done.

``````
hab@laptop {~}$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
pan0      no wireless extensions.

```

---

### Post by chili555 on 2010-06-14
```
FATAL: Unknown capture source type '[COLOR="Red"]AR5B95[/COLOR]' in source 'AR5B95,wlan0,Wifi'
```What is wanted is the driver name, not the card name. Your driver name *might* be ath5k. Find out with:```
sudo lshw -C network
```Here is an example from mine:> *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       logical name: wlan0
       --- snip ---
       configuration: broadcast=yes [COLOR="Red"]driver=iwl3945[/COLOR] ip=192.168.1.108 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:32 memory:edf00000-edf00fffOnce you confirm your driver name, amend your kismet.conf and send me a copy of your M.S.```
ath5k,wlan0,Wifi
```

---

