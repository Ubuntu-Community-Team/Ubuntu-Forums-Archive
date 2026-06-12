---
title: "Home Networking/Firewall Help Request"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by darrengreer on 2009-05-20
Okay, so I've decided to complicate my home network even further, since it wasn't complicated enough.  Here is what I am trying to do visually:

CableModem --> AirportExtreme(802.11n)(10.0.1.1) --> N Clients(10.0.1.x)
                                                 |
                                                 |--> UbuntuFirewall --> Linksys(802.11b/g)(192.168.1.1)  --> b/g Clients(192.168.1.x)

(Note: Visually it is not working, that UbuntuFirewall is hanging off of the AirportExtreme)

I have the first portion working for the N clients, but having difficulty figuring out what I need to do on the UbuntuFirewall and Linksys router.

DHCP is running on the AirportExtreme obviously.  The UbuntuFirewall has 2 ethernet ports.  I am assuming I should statically assign the external port something like: 10.0.1.2.  Then, here is my confusion.  Should I have my UbuntuFirewall handing out DHCP on something like 192.168.1.x and put the Linksys router in bridge mode? Or, do I leave the linksys router in AP mode handing out its own DHCP addresses?

Any help would be greatly appreciated.

---

