---
title: "Kismet Configuration"
date: 2009-05-24
forum: Networking &amp; Wireless
---

### Post by yvenard on 2009-05-24
I having trouble getting kismet to work. For the source, I have typed:"source=AR5001X+,wlan0,Atheros" and got the following error when I tried t run kismet
root@iTech:/home/yvenard# sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'AR5001X+' in source 'AR5001X+,wlan0,Atheros'
Done.
I have tried this source also: " source=ath5k,wlan0,atheros" i am not getting any. 
I am using EnGenius Ultra long range Super G Wireless PCI card (EPI-3601S).
Any help will be very appreciate.
Thanks,

---

### Post by chili555 on 2009-05-25
> source=ath5k,wlan0,atherosThis is more likely to be the correct line. Let's find out what driver your card is using:```
sudo lshw -C network
```Your Atheros will show up, as well as your ethernet, which we can ignore. You need the interface name, presumably wlan0, but maybe not; as well as the driver name, presumably ath5k, but maybe not. Those are the details that need to be matched exactly in *sources=*.

After you make any changes, post back any errors.

---

### Post by yvenard on 2009-05-26
I am sorry the fact it took me a while to get back to you. I have applied it and everything is working fine. Thanks for your support.

---

