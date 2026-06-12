---
title: "Kismet configuration wifi card"
date: 2012-11-25
forum: Networking &amp; Wireless
---

### Post by tfdelaney on 2012-11-25
Hi,
I'm trying to run kismet with a wifi card on wlan0. I keep getting the following reply when i sudo kismet....
"FATAL: Unknown capture source 'rt2800usb' in source 'rt2800usb,wlan0,rt2800usb'.
 
I've tried everything. Have no idea what to do. Any help would be greatly appreciated. I know I'm doing something wrong with the kismet.conf file, but don't lnow at this point.
Thanks

---

### Post by chili555 on 2012-11-25
According to the README, rt2800usb is not a recognized capture source. Please see Section 12:```
less /usr/share/doc/kismet/README.gz
```Not all wireless devices do all things; in this case, monitor and channel hop.

---

### Post by tfdelaney on 2012-11-25
What do you mean by monitor and channel hop?    Consider me a novice.  Doing this for a grad school project, and am trying to get KIsmet started so that I can monitor traffic with a GPS.

---

### Post by chili555 on 2012-11-26
The card needs to be able to switch to monitor mode, that is, just listen to traffic and don't attempt to connect. Moreover, it needs to be able to be manipulated by Kismet to channel hop; to listen first on channel 1 and then 2 and then 3, etc. The rt2800usb card and driver combinations either can't do so at all or haven't been sufficiently researched and written in to the Kismet code. 

A great many cards do some features but not all. Many very inexpensive cards *only* connect to a router and have no additional features at all! The good news is it's a USB card, you can pull it out and try a better suited card easily. No screwdriver or maintenance manual required.

---

