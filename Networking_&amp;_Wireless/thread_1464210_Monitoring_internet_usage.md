---
title: "Monitoring internet usage"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by keshav_57 on 2010-04-27
Hello

I have two internet connections. A WiFi, and a USB stick. 
I would like to monitor the usage from each of the internet connections separately. 
Currently I use vnstat for the same. 
vnstat -i eth1 gives me the usage. However, I am not sure whether this gives the usage for Wifi, or the total usage for both connections. 

Any help is appreciated. 
Thanks.

---

### Post by mcoleman44 on 2010-04-27
Try using wireshark. And Im not sure how that works.
Is the usb have an antenna that picks up a wireless connection? Because I dont think a computer can have more than one IP at a time. So it would be hard to filter the results for one IP.

---

