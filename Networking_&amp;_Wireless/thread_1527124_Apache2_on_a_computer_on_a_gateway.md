---
title: "Apache2 on a computer on a gateway"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by Nyken on 2010-07-08
I have Ubuntu 10.4. My computer is connected to AT&T U-verse on a 2Wire brand Residential Gateway. The RG has the actual IP address. It's assigned my computer the address 192.168.1.66.

I want to run the apache server to share files between my two computers across town. My other one is directly connected to the internet with a DSL modem so it's IP is static and was easy to set up and get going. What I want to know is what do I type to access my apache server on my RG? Galactic newbie here.

Thank you in advance!

---

### Post by Yarui on 2010-07-08
You will probably need to get into your gateway, probably at IP 192.168.1.1, and forward the necessary ports to your apache2 server.  You will at least want port 80 forwarded to your server for HTTP, and ports 20 and 21 if you want FTP traffic to go to your server as well.  This should make it possible to just type in your gateway's outside IP address and connect directly to your webserver over the internet.

---

### Post by Nyken on 2010-07-08
Pointed me in the right direction. Got it all setup and working now. Much thanks!! :D

---

### Post by Yarui on 2010-07-08
No problem, you should mark the topic [solved] if you don't need any more help.

---

