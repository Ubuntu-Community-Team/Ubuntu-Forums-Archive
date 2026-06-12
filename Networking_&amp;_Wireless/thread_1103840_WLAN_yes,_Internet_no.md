---
title: "WLAN yes, Internet no"
date: 2009-03-23
forum: Networking &amp; Wireless
---

### Post by AndyM3 on 2009-03-23
Hello,
I have a problem with my network connection. I can connect to my wireless network but I can't connect to the Internet. When I want to update the repositories, it works for like 6 seconds, then gives a "113 no route to host" error.
It didn't work at all before setting the nameservers to OpenDNS. Could that be a problem?
I have an Eee PC 4G Surf (701) and a Belkin G Plus router. Is the fact that I've set my router to use the G+ mode a problem? My Eee runs Eeebuntu Base. I use WPA-Personal and AES encryption (TKIP didn't work at all).
Sorry if this has been asked (and resolved) before!

---

### Post by AndyM3 on 2009-03-23
Someone? Please help! I just installed Easy Peasy and de-activated my router's firewall, it worked for like 1 minute and then ping said it could ping google and google would respond, but apt-get update failed, Firefox failed, Songbird failed (can't resolve IP).
EDIT: I think i've solved the problem now, did a "iwconfig wlan0 rate 24M" and everything seems ok.
EDIT2: Not fixed :( :( :(

---

