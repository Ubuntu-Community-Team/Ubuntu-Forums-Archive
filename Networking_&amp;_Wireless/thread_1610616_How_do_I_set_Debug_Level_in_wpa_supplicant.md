---
title: "How do I set Debug Level in wpa_supplicant?"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by not_a_phd on 2010-10-31
Have been trying to diagnose why my wpa_supplicant keeps disconnecting my eepc901 wireless (rt2860sta driver) every 5 seconds with the following cryptic /var/log/syslog message:

```
Oct 31 22:36:13 jim-laptop-0 wpa_supplicant[2439]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```

Tried to increase the debug output from these events by issuing the following command:
```
wpa_cli -i ra0 
```

and got no joy. The wpa_cli could not connect to wpa_supplicant. 

While I am quite grateful that the NetworkManager manages to respool my wireless connection after wpa_supplicant hoses it, I would like all this background nastiness to stop.

---

### Post by not_a_phd on 2010-11-01
Good morning East Coast USA! Lots of views of this topic... any suggestions?

---

