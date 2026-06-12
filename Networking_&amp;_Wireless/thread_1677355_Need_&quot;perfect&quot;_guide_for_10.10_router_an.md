---
title: "Need &quot;perfect&quot; guide for 10.10 router and firewall"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by jubajuba123 on 2011-01-28
So yeah, like the title says... Can someone post the "perfect" tutorial for setting up a router and firewall for Ubuntu 10.10 Server 64-bit?
I'm kind of a n00b when it comes to Linux, so I get really confused with some things, which is kinda why I need help here... I have seen things on the ubuntu wiki about this... but it really confuses me =\

I'm trying to setup my ubuntu sys as a router and firewall...
Internet -> Ubuntu (Router) -> Switch (no DHCP on it) -> Computers
I've already setup bind and dhcp3 and got those working perfectly... I've also setup Squid3 and Dansguardian for content filtering (blocking ads and such) and got them working too...
I want to set it all up to be transparent, and allow the system itself to function as a powerful firewall router, giving absolutely NO issues to client computers connected, and no speed reduction at all....
I want to setup the firewall to allow all outgoing connections, but block everything incoming (stealth the network)... Forcing all http/s traffic to pass through dansguardian, then to squid...

But am very confused on how to pull this off...

The system is running Ubuntu 10.10 Server 64-bit, with 4 GB of RAM, 320 GB SSD, and two 1Gb NIC cards...

Sorry if I'm not very clear, I do speak english perfectly, but just kinda new to the "Linux world", I was using SONICWALL but that's getting a little too costly to my network and wanna do a free alternative... Something completely CUSTOM, not using some network security distro... So please dont tell me to use something else, I want to do this myself for both learning purposes and for the fun of it lol...

Thanks!

---

### Post by JonathanN on 2011-04-08
(it seems like you just need to set up Iptables to redirect ip traffic the esiest way is to get firehol. I presume you have set squid to transparent)
sudo apt-get install firehol
sudo nano /etc/firehol/firehol.conf
(add  the following lines just be carefull to use the correct eth#)
transparent_squid 8080 "proxy dansguardian root" inface eth(filter side) <this sorts out port 80 also why its not bellow>
transparent_proxy "443 3128(anything else you want to proxy)" 8080 proxy dansguardian root" inface eth(filter side)
interface eth(filter side) Lan
              server all accept
              client all accept
interface eth(WAN side) WAN
              policy drop
              protection strong
              server "(list services by name you wish to contact from outside)" accept
              client all accept
router (give name) inface eth(filter side) outface eth(WAN side)
              masquerade
              route all accept
router (give name2) inface eth(WAN side) outface eth(filter side)
              route all accept
(save and start firehol)

this shuld make the dansguardian transparent "webpages etc" and allow other services to run around the out side such as voip

---

