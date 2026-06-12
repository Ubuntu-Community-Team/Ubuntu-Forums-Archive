---
title: "Wireless alternate between connected &amp; disconnected!!"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by ssalman on 2006-02-28
After much trial and error I was able to setup my new wireless card (Netgear WG511T) with WPA_supplicant... But I'm having the strangest problem, my connection keep on alternating between connected and disconnected states. Each state stay for few seconds. This makes browsing the net extremely slow.

I went into wpa_cli to check what is going on, and here is what it is telling me:
  
```

<2>CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
<2>Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxxxxxx' freq=2452 MHz)
<2>Associated with xx:xx:xx:xx:xx:xx
<2>WPA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=TKIP GTK=TKIP]
<2>CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:xx:xx completed (reauth)
<2>CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
<2>Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxxxxxx' freq=2452 MHz)
<2>Associated with xx:xx:xx:xx:xx:xx
<2>WPA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=TKIP GTK=TKIP]
<2>CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:xx:xx completed (reauth)
<2>CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
<2>Trying to associate with xx:xx:xx:xx:xx:xx (SSID='xxxxxxxx' freq=2452 MHz)
<2>Associated with xx:xx:xx:xx:xx:xx
<2>WPA: Key negotiation completed with xx:xx:xx:xx:xx:xx [PTK=TKIP GTK=TKIP]
<2>CTRL-EVENT-CONNECTED - Connection to xx:xx:xx:xx:xx:xx completed (reauth)
<2>CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
``` 

I would appreciate any help guys... Thanks.

---

### Post by ssalman on 2006-03-01
Anyone??

---

### Post by ssalman on 2006-03-03
anyone... is there a forum for wpa_supplicant??

---

