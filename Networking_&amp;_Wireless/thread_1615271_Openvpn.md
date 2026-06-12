---
title: "Openvpn"
date: 2010-11-06
forum: Networking &amp; Wireless
---

### Post by Mr.O on 2010-11-06
I was wondering where there was a guide for all of the options of the openvpn scripts so that I can get the server to do exactly what I want to do. 
Mr. O

---

### Post by SeijiSensei on 2010-11-08
openvpn.net has a lot of helpful documentation.

---

### Post by Mr.O on 2010-11-08
What I want to do is to have the darn thing run as a router and that access to the network is encrypted. If they can get the correct key and other things then it works like I just plugged the darn thing into the local network. That is what I am after. I dont mean to be rude but redirecting me to the site that made it is an exercise in the obvious. I was asking for the DOCUMENTATION not the website that it is hosted on!

---

### Post by SeijiSensei on 2010-11-08
Excuse me, but how is this not a reply to your request for "a guide for all of the options of the openvpn scripts so that I can get the server to do exactly what I want to do."

Did you even browse the documentation they provide?  It's *very* extensive.

[HOWTOs](http://openvpn.net/index.php/open-source/documentation/howto.html)
[Complete Documentation Tree](http://openvpn.net/index.php/open-source/documentation.html)

Since only you know what you want to do with OpenVPN, only you can answer your question.

---

### Post by Mr.O on 2010-11-08
All I want to know is if it is possible to have a vpn connection to a server and have only the ENCRYPTION handled by the vpn server, no bridging, no dhcp, no special routing to get to the local network. Is that possible.

---

### Post by SeijiSensei on 2010-11-08
I'm still not entirely clear on what you want to do, but if you're asking whether you can set up a point-to-point encrypted connection between two machines over an OpenVPN tunnel, then the answer is yes.  The simplest method is to use a shared encryption key as described [here](http://openvpn.net/index.php/open-source/documentation/miscellaneous/78-static-key-mini-howto.html).

---

