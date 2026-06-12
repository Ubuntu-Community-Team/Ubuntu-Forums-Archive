---
title: "using ics between two desktops"
date: 2009-05-19
forum: Networking &amp; Wireless
---

### Post by dubesinhower on 2009-05-19
i have two nics on my main desktop. this desktop uses the windows 7 release candidate.
the nic i use to connect this desktop to my router has a static ip. 
i would like connect the second nic to my other desktop, running ubuntu 9.04, using ics in windows 7.

what should i set for the ip, subnet, gateway, and dns on my second nic on my windows 7 machine, and what should i do on my ubuntu machine to use this connection?
thanks for the help in advance. :)

---

### Post by dmizer on 2009-05-20
Any [private IP address](http://wiki.answers.com/Q/What_is_a_nonroutable_IP_address) will be fine, as long as it's in a different [subnet](http://en.wikipedia.org/wiki/Subnetwork) than the network adapter that connects to the internet (eg: 10.0.0.1)

Netmask will automatically data filled. Gateway will be the ip address of your external web gateway. This could be either a router (eg: 192.168.1.1), or your external WAN IP address.

---

### Post by dubesinhower on 2009-05-20
it turns out that my second nic in my main pc does not work at all. thats why ive been having issues.
im going to install a second nic into my ubuntu machine instead. can i do ics through my ubuntu machine?

---

### Post by dmizer on 2009-05-20
Yes you can. Have a look here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

