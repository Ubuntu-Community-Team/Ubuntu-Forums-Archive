---
title: "Configuring wireless connection from command line on ubuntu server"
date: 2013-02-15
forum: Networking &amp; Wireless
---

### Post by Warlon on 2013-02-15
Hi,

I'm running ubuntu server edition on an old eeepc -laptop and I whould like to know how can I add and configure a wireless network connection from the command line? The network is not available to me, but I would like to add it in advance so that the laptop would connect to it automatically once it finds this network.

How can this be done? Security settings for this networks are "WPA2-personal" and encryption "WPA-TKIP or WPA-AES". I also know the network's name and passphrase.

---

### Post by ali abry on 2013-02-15
you can connect to wirless by using **iwconfig** and find avalable networks with **iwlist**

```
 $ iwlist wlan0 scanning 
``````
 $ iwconfig wlan0 essid  keypassword
```actually i don't now how to connect automatically .

---

