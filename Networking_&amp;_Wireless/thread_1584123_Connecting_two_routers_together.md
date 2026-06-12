---
title: "Connecting two routers together?"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by miggols99 on 2010-09-28
I don't really know much about networking, so don't get too complicated...

I have two wireless routers, one ADSL one next to the phone line, and one down in my games room, connected to the ADSL one via ethernet. The wireless from the one next to the phone line doesn't reach the games room - this is why I bought the other router. Now, my question is, I want to be able to connect to the computers connected to the ADSL router when I'm connected with the one in the games room. With my current configuration, I get a page not found error if I simply try to connect to the router and ping gets no reply.

So what do I have to do to be able to do this? Is this possible with what I have?

---

### Post by blakep2 on 2010-09-28
Ok the one connected to the adsl line is assigning dhcp more than likely. Run a ethernet cable to the one in the game room from the phone line router's lan port to a lan port on the game rooms router.  Set up the router in the game room to a ip not in the dhcp range.  So if the phone line router is using the ip 192.168.1.1 and assigns through 192.168.1.100-150.  Then the router downstairs can be assigned the ip 192.168.1.2.  Make sure to turn of dhcp on the game room router.  Use the same ssid on both and use different channels on frequencies.  

It is a bit of a technical process but if you have any questions please ask.  I have this set up at my house and the company I own sets these situations up.

---

### Post by perspectoff on 2010-09-28
Also see more info on nested routers at:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Using_a_nested_wireless_LAN_router](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Using_a_nested_wireless_LAN_router)

or

[http://kubuntuguide.org/Lucid#Using_a_nested_wireless_LAN_router](http://kubuntuguide.org/Lucid#Using_a_nested_wireless_LAN_router)

---

### Post by blakep2 on 2010-09-29
I dont think he is looking for a nested router.  I believe he is just looking for a secondary access point to expand his range.

---

