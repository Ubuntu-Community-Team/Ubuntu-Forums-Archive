---
title: "No Detect Linksys"
date: 2006-02-28
forum: Networking &amp; Wireless
---

### Post by nyfeh on 2006-02-28
I'm running breezy 5.10 64bit on an AMD 2000 Xp. I cannot get the wifi internet to work with a WMP54gs card. The card in lspci shows 0000:00:0d.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
or atleast thats what I think it is...

If someone could help I would greatly appreciate it as I am quite lost.
I've tried installing the drivers that came with the linksys install cd via ndiswrapper but wlan never shows up in iwconfig or System>Admin>Networking.

---

### Post by ssam on 2006-02-28
the next version of ubuntu (dapper drake) in april should have drivers for broadcom cards.

---

### Post by nyfeh on 2006-02-28
Is there anything I can do until then?

---

### Post by ssam on 2006-02-28
someone may be able to help you set up ndiswrapper

---

### Post by arckeda on 2006-02-28
I dont think thats your problem, i thought my adaptere was not detected too, try setting up your card but not activating it, then go to root terminal and type:

iwconfig wlan0 essid any ap any


 then activate that might fix it

---

