---
title: "Network Issues"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by -John- on 2010-05-03
I just upgraded to Ubuntu 10.04 My problem is that Irc will not connect. None of my Empathy accounts will Connect. but at least some Websites seem to connect just fine through firefox. though not all as far as I can tell. I am behind a Linksys Wireless-G Router. This is a Wired Connection connecting to DSL. It is not the network card as I tried a spare with identical results. also IPV-6 is set to ignore. 

pinging [www.google.com]("http://www.google.com") through command line shows 100% packet loss. however I can connect to [www.google.com]("http://www.google.com") easily in firefox.

No apparent difference with direct wired connection to modem. 

no Difference With Wireless USB Adapter. Considering fresh Install. 

Removing And Re:installing Network-Manager through Command Line Seems to have helped. Oddly it did not help doing it through the Ubuntu Software Center.  

Any help or suggestions would be Highly Appreciated.  Thanks A Lot.

Thanks For Everyone's time.

---

### Post by Iowan on 2010-05-03
Any difference if you ping by IP address? (74.125.95.106)

---

### Post by stormcel on 2010-05-03
try pinging the above address and see if the issue is dns or gateway
if the ping fails try:

sudo route add default gw (ip here) (interface here)
example
sudo route add default gw 192.168.1.1 eth0
this is what happened to me, dhcp worked, but no gateway

---

