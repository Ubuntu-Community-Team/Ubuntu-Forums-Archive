---
title: "Could my ISP be blocking vnc ports 5500 and 5900 from me?"
date: 2009-05-29
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-05-29
I want to make this as short as I can so it doesn't come across as long winded:

-I have just bought a new router from Netgear, a WPN824 v3.
-The firmware is up to date
-I have port forwarded ports 5500 and 5900 to my main PC
-I have setup my dyndns.org login info within the router and it shows a successful update of my external IP when I check its status.
-Attempting to access my PC from my laptop over the LAN works just fine, and vice versa
-Attempting to access my PC from either itself, or the laptop using the dyndns.org domain gives me a Connection Refused (111) error message
-I have configured the firewall on both the laptop and the PC to accept inbound connections on 5500 and 5900 from all hosts.
-I can ping the router using my dyndns.org domain name
-After setting up port forwarding, but before I configured the dyndns login, attempting to access using VNC and the domain name.  It would not produce a Connection Refused error message, but would just hang as if it wasn't getting a connection refusal or connection of any sort.
-I changed my port forwarding to point to my laptop instead of my PC and attempted to test using the dyndns domain name again, but I get the same error message.
-I once temporarily configured the router to make my home PC a DMZ server (which I've never done before, so I don't understand what it's for completely, but the theory was it would bypass port forwarding all together) but that didn't help any, so it's since been disabled.
-On the side, I also get connection refusal if I try to SSH to my PC using the dyndns address.

Not sure what else to try or check.

---

### Post by DGortze380 on 2009-05-29
they could be, but i doubt it.

sounds like a port forwarding issue.
check everything via LAN first, get vnc working.
then check your port forwarding settings.
try vnc via your external IP
try vnc via your dyndns name

just out of curiosity, when you log into your routers configuration page, it should tell you the external IP of the router.

please check that ip, and compare it to the information from this web site: [http://www.whatismyip.com/](http://www.whatismyip.com/)

post back and let me know if they match.

---

### Post by Sooner Al on 2009-05-29
Its possible your router does not support calling back to your LAN via a loopback. Many consumer grade routers don't.

[http://theillustratednetwork.mvps.org/Vista/PPTP/BasicVPNTest.html]("http://theillustratednetwork.mvps.org/Vista/PPTP/BasicVPNTest.html")

Verify port forwarding by going to the [http://www.canyouseeme.org]("http://www.canyouseeme.org") site and running the test for both ports from the PC the VNC server is running on. If the test passes then port forwarding on your router is OK and you need to test from a true remote location, ie. friends house, public hot spot like a bar/restaurant, etc.

---

### Post by diablo75 on 2009-05-29
Solved.

Replaced the netgear with a linksys.

I've gone through three netgear routers in two weeks.  Never had a problem with port forwarding 5500 or 5900 for VNC purposes until today.  Hopefully I never will have that problem again with this linksys.

---

