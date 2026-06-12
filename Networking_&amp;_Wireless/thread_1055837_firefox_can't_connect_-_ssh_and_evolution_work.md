---
title: "firefox can't connect - ssh and evolution work"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by vase on 2009-01-31
First when I connect to the same network with a wired connection I have no problems at all.

Strange things happen when I try the wireless network, I use the following procedure to connect:

#! /bin/bash

iwconfig eth1 essid "bart-draadloos"
wpa_supplicant -i eth1 -c /etc/wpa_supplicant/wpa_psk.conf -B
dhcpcd -d eth1

After this script I have a connection (I can login to a server with ssh, check my mail, but not send mail), in firefox I can't connect to any website.

Any suggestion?

---

### Post by vase on 2009-01-31
My brother helped me out. In firefox I typed aobut:config, and then put ipv6disabled to true. After this firefox worked again.
We don't really understand why this solved the problem so an explanation would be nice.

---

### Post by Another Monkey on 2009-01-31
Shot in the dark - does your wireless support ipv6?  "ifconfig -a" give any clues to that?

(I am still trying to suss networking, but in my latest fight with wireless I noted that the ipv6 setting vanished from the ifconfig output at one point; they're back now)

---

### Post by vase on 2009-02-13
now ipv6 is disabled in firefox but is not working...
ssh en evolution are still working
Any suggestion on how I can diagnose this problem?

update0: I tried doing dnslookup on another computer and typed that in 
firefox, now I can go to google for example using the ip adres I get from that

nslookup on my ubuntu pc gives me nothing...

uptate1: It appeared to be the DNS server, I added the adres to /etc/resolv.conf.

---

