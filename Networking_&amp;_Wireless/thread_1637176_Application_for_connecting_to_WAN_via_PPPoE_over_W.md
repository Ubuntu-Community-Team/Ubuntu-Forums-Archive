---
title: "Application for connecting to WAN via PPPoE over WLAN"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by nikkae on 2010-12-04
Does anyone know of an application other than NetworkManager that will allow me to connected to WAN via PPPoE over WLAN?

---

### Post by phoenixpb on 2010-12-04
opss sorry a moderator can delete the answer ?
reply here because the two questions are similars

---

### Post by dineshs on 2010-12-04
> Does anyone know of an application other than NetworkManager that will allow me to connected to WAN via PPPoE over WLAN? 
I dont think NM can do that.There is a command line way.Configure your connection using
```
sudo pppoeconf wlan0
```(assuming wlan0 is the wireless interface)
To connect run ```
pon dsl-provider
```and to disconnect```
poff dsl-provider
```

---

### Post by nikkae on 2010-12-04
pppoeconf causes problems with NetworkManager/NetworkManager-applet 0.8.0 as they ignore the network connection as they perceives them be manually configured (NetworkManager & NetworkManager-applet have been programmed to ignore manually configured connections).

---

### Post by dineshs on 2010-12-05
> **nikkae said:**
> pppoeconf causes problems with NetworkManager/NetworkManager-applet 0.8.0 as they ignore the network connection as they perceives them be manually configured (NetworkManager & NetworkManager-applet have been programmed to ignore manually configured connections).This is because running  pppoeconf command adds some lines in /etc/network/interfaces
To solve this first configure the connection using *sudo pppoeconf wlan0* Then edit /etc/network/interfaces so that it contains only the following lines (before editing you may backup the file)
```
auto lo
iface lo inet loopback
```
Restart the machine and see if both pon dsl-provider and NM  works

---

