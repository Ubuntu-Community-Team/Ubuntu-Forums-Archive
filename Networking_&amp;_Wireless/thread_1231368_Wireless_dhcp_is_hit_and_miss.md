---
title: "Wireless dhcp is hit and miss"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by alleycatuk on 2009-08-04
Hi,
I'm reasonably new to Ubuntu - just installed 9.04 and am having mixed results with a wireless set up that I know works ok under XP.
I've followed loads if how-to guides and made progress as far as:
ndiswrapper is working fine
wpa_supplicant is configured and as far as I can tell works ok
 
getting a DHCP lease is very hit and miss - works sometime and not others. I can't get wpa_supplicant to work on the daemon but if I run it in a terminal, it always says "WPA key negotiation completed" followed by "connection to <router's MAC> completed. So it can see the router and seems happy with the psk.
 
if I do a "sudo dhclient wlan0" it sometimes gives me an address and sometimes doesn't. If I kill wpa_supplicant, take wlan0 down then run wpa_supplicant and take the interface up then dhclient again, it works more often than not but not always.
 
 
 
 
 
 

I've spent 10 days looking through countless posts many of which have helped get me to where I am now (which is an occasionally working wireless!) but can't find anything that will sort out the 2 problems, namely:
[LIST]
[*]dhcp doesn't find an address every time
[*]it won't all run on boot up
[/LIST]THe set up obviously works as I can get to wireless but something is happening to make it only occasional. Any suggestions are welcome as I've now run out of ideas.
 
My set-up is: Ubunty 9.04, ndiswrapper, wpa_supplicant, Linksys WMP54G (shows as Broadcom Airforce One 54g in lspci) and router running WPA2 AES.

---

### Post by alleycatuk on 2009-08-04
More info... when dhcp fails, I can't even ping the router. It comes up with "Network is unreachable" even though wpa_supplicant can see the router and is handshaking with it.
I tries to do a "route add" to add the gateway but it came up with SIOCADDRT: No such process

---

