---
title: "2 internet connections - require one as failover"
date: 2011-11-24
forum: Networking &amp; Wireless
---

### Post by Chumber on 2011-11-24
Hi,

I have two internet connections in my home: 1 ADSL and 1 cable. I have a computer with Ubuntu installed on it, and it is connected directly to my modem via ethernet (eth0). However, if the cable connection fails (as occasionally happens) I want it to switch to wlan0 and use my ADSL connection until the cable begins working. How would I achieve this?

I've looked at various load balancing and failover software packages, but these seem to be overly complex - is there a simple method that I could use to achieve the above aim?

Thank you for reading my post and to anyone that can offer any assistance!

---

### Post by ptrakk on 2011-11-24
with network manager you could just connect to both of them. make sure your dsl modem is set up as bridge mode(dhcp mode) instead of pppoe for less hastles.

---

### Post by Chumber on 2011-11-24
> **ptrakk said:**
> with network manager you could just connect to both of them. make sure your dsl modem is set up as bridge mode(dhcp mode) instead of pppoe for less hastles.

I tried this initially, but network manager only uses one of the networks for the internet (which is eth0). Furthermore, there is no way of my box knowing that eth0 is down through the network manager, and that it should switch to wlan0.

---

### Post by Chumber on 2011-11-25
Apologies for shamelessly promoting this thread, but I need an answer! Thanks!

*bump*

---

