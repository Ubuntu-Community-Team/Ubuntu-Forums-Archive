---
title: "wifi Radar and Broadcom chipset"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by Riona on 2006-06-17
I downloaded wifi radar to try and connect via wpa. In the setup when selecting use WPA it asks for a driver. Do i copy the bcmwl5.sys driver into it? 
Right now I'm connected using network manager and bcm43xx-fwcutter. followed a howto for broadcom wireless cards.
Thanks

---

### Post by xXx 0wn3d xXx on 2006-06-18
Try using wpasupplicant:
> sudo apt-get install wpasupplicant

---

### Post by Riona on 2006-06-18
It's installed. I went threw the setup and i'm unable to ping the router. 
the ssid is broadcasting it's not hidden.

---

### Post by darkshadow on 2006-06-18
To quote the official bcm43xx website

"You must remove wifi-radar, as it has a driver conflict with the driver."

basically don't use wifi-radar

---

