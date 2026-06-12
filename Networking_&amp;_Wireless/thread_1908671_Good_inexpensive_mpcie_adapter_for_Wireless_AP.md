---
title: "Good inexpensive mpcie adapter for Wireless AP"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by bakegoodz on 2012-01-13
I looking to roll my own wireless access point with a mini-itx system I'm no longer using. I'm looking for a mini pcie adapter that supports 5 ghz 80211n. I found a Intel 6200 for $28 on NewEgg. It does have a mac80211 kernel driver, which is what hostapd program requires, but I'm still not sure if it supports AP mode or not. Other hardware (atheros) I can find is about $60 on from special wireless resellers, but their high power for long distance applications and this just for my 1500 sq/ft 1 level home. Anybody have recommendations or know for sure what hardware supports AP mode in Linux?

---

### Post by bakegoodz on 2012-01-14
Found out that Intel won't work from this page
[http://linuxwireless.org/en/users/Drivers](http://linuxwireless.org/en/users/Drivers)

---

### Post by bakegoodz on 2012-01-14
Found a couple of adapters, not very cheap to go dual band 80211n about $40 to $45 is the cheapest I could find.

Atheros mpcie card 
[http://goo.gl/U48yJ](http://goo.gl/U48yJ)
and couple of Ralink based USB adapters
[http://goo.gl/KMPva](http://goo.gl/KMPva)
[http://goo.gl/dzLxD](http://goo.gl/dzLxD)

---

### Post by bakegoodz on 2012-01-23
I got the Asus USB-N53 Ralink RT3572 based adapter. What a pain! I had to upgrade the firmware file under /lib/firmware before it would even work. (With latest 11.10 kernel) I couldn't ever get 5 ghz to work. I'm sending the USB adapter back and sticking with Atheros. I might be getting this one [http://www.streakwave.com/itemdesc.asp?ic=SR71E&eq=&Tp=](http://www.streakwave.com/itemdesc.asp?ic=SR71E&eq=&Tp=)

I'm not promoting the vendor, I will look for another. I cancelled my last order because it was 5 weeks back ordered and they didn't tell me until I called twice about the status.

---

