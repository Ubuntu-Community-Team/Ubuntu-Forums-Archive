---
title: "Dell 1320c Printer network not being found"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by terbor on 2009-11-09
I have the a dell 1320c hooked up to my network.  I logged into the dell interface and set the IP address.  I have tested the printer via usb so I know it works.  

I set the IP through system -> administration -> printing Device URI to be socket://192.168.1.22:9100 and I log into cups via localhost:631 and I can see the printer and it says that the printer is unplugged or turned off which it is neither.  

I have tried restarting it I am out of ideas on why cups thinks the printer is off.  Any ideas?  Thanks for any assistance.

---

### Post by terbor on 2009-11-09
I figured it out.  There is a start printer option in the cups page localhost:631 ....

---

