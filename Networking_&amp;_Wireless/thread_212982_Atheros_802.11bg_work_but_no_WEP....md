---
title: "Atheros 802.11bg work but no WEP..."
date: 2006-07-10
forum: Networking &amp; Wireless
---

### Post by shooterae5 on 2006-07-10
this card worked great under Ubuntu 5.04. now under Dapper (clean install from CD). I can connect to my AP as long as I do not use WEP.

I've entered the key several ways: 
&#65279;	03CC74C2866AF519BACC38493F
	---
	03CC 74C2 866A F519 BACC 3849 3F
	---
	03CC-74C2-866A-F519-BACC-3849-3F

using both hex and ASCII and I can't get an IP address. 

So have to turn off wep to connect or us hard wire. 

I'm thinking I'm missing the encryption package...
Could someone tell me what packages I should have and then we can go from there.

---

### Post by Eversmann on 2006-07-10
Using iwconfig athX key "key", the first one you posted is correct.

A solution could be stop using the restricted drivers that comes with dapper (madwifi-old) and install the latest from [www.madwifi.org](www.madwifi.org). Instructions on how to install it are on that site. Don't forget to disable the current drivers if you do not uninstall restricted modules at /etc/default/linux-restriced-modules-common

---

