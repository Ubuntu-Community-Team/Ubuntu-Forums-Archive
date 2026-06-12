---
title: "wifi ssid change"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by u_kapaley256 on 2009-11-26
Hi,
I use ubuntu 8.04 with wicd for connecting to wireless networks.I can also use use wpa_supplicant from the command line.Recently my roommates changed the ssid of the wpa2 network which totally messed up my system.Now it takes a lot of time to dhcp ( if it is going to)and i can see the old ssid in the wicd while it shows the new ssid in the status.Even after connecting its very sluggish and monitoring the interface gives a feeling that its on-off connectivity.

Sorry for being wordy

please help

Udayan

---

### Post by u_kapaley256 on 2009-11-26
I got it.
I simply removed the wicd and reboot and connect through wpa_supplicant command line worked wonders.
Maybe it is because i was still connected through the wicd when the ssid was changed and that is why it was always confused between the old ssid and the new

Thanks for the views.

---

