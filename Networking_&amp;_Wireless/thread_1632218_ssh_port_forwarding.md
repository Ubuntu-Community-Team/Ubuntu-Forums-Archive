---
title: "ssh port forwarding"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by nbo10 on 2010-11-27
Hi All, trying to to set up ssh so that I can login to my laptop from other locations. I have a dsl modem and wrtu54g wireless router. My laptop is set to a static ip address 192.168.28.110. The router ip address is set to 192.168.28.28. The dsl modem pages shows that the router address is 192.168.1.30???

I've set my router to forward port 22 to 192.168.28.110. I've tried forwarding port 22 on the dsl router to both 192.168.28.28 and 192.168.1.30. But when I try "ssh IP_address_dsl" I receive "ssh: connect to host ipaddress port 22: Connection refused"

What am I missing?

---

### Post by nbo10 on 2010-11-27
Okay, I bridged the modem and router. Now I'm getting a timed out connection to the ssh request.

---

### Post by nbo10 on 2010-11-27
Nevermind. Everything is working. I forgot to put in the new ip address that the router was assigned.

---

### Post by Jlayman on 2010-11-27
is this just on a lan or are you trying to access from anywhere?  I only wonder because the static ip address you listed seems to be local.  meaning you wont be able to access it over the internet unless your in your lan.

---

