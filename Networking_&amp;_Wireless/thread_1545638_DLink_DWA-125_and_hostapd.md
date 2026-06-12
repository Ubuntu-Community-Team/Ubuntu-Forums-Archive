---
title: "DLink DWA-125 and hostapd"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by y50a7XpWRH66IV on 2010-08-04
Hi all,

I am currently trying to get my DWA-125 USB wireless adapter to work as an access point with hostapd.

I was able to configure and set up the card using: [http://ubuntuforums.org/showpost.php?p=9632897&postcount=15](http://ubuntuforums.org/showpost.php?p=9632897&postcount=15)

I then installed hostapd and followed this guide to set up the hostapd configuration: [http://blog.bokhorst.biz/3395/computers-en-internet/](http://blog.bokhorst.biz/3395/computers-en-internet/)

The problem is that when I attempt to start hostapd, i get:

```
Configuration file: /etc/hostapd/hostapd.conf
ctrl_interface_group=0
nl80211 not found.
nl80211 driver initialization failed.
wlan0: Unable to setup interface.
rmdir[ctrl_interface]: No such file or directory

```

Does anyone know what this is happening and how to fix this?

Thank you :p

---

