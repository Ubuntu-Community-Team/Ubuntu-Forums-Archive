---
title: "load balancing 2 NICs"
date: 2011-09-16
forum: Networking &amp; Wireless
---

### Post by Jethro_uk on 2011-09-16
I'm running 9.10. I have 2 NICs, eth0, and wlan0.

eth0 is an onboard ethernet connection and goes direct to the internet via routerONE

wlan0 is a wireless PCI card, and is connected to routerTWO.

routers ONE and TWO have separate internet capabilities. ONE is my domestic cable BB. TWO is my work-supplied ADSL connection.

Currently I work from home. My work Laptop connects to routerTWO, and through there I can NX and SSL into my 9.10 box.

I mainly use the 9.10 box for downloading. Currently I have set the network up (using the GNOME NM) so that wlan0 has "only use this connection for resources on this network" set. I am assuming that this will force all internet traffic to go via routerONE and eth0.

Is it possible to set things up so that any "spare" internet capacity on routerTWO can be given to wlan0, without affecting my laptop ?

---

