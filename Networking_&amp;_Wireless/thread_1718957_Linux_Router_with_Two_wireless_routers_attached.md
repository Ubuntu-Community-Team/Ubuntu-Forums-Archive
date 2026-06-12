---
title: "Linux Router with Two wireless routers attached"
date: 2011-04-01
forum: Networking &amp; Wireless
---

### Post by Aestas44 on 2011-04-01
First and foremost, I apologise if this question has already being asked or if this is the wrong section to ask for help. 

Recently my last router died (3rd one in the last 12 months), and I am looking at replacing it with a more powerful Linux router. My home network has more than 15 devices (computers, various network drives, phones, etc) attached, and hence it has extremely heavy levels of traffic. 

Although I'm yet to set up a computer with Linux as a router, it seems I will be able to set up the router bit. What I can't work out is that once the Linux computer is set up, how to get it to talk to the two wireless routers (Netgear .... and yet-to-be-bought) without everything 'breaking'. 

Is it worth (the time spent) using a Linux computer as a router and do you think this architecture is 'best'?

                    
Modem 
-> Linux Router 
-->Switch --->everyone else on wire
-->wireless router 'b'
-->wireless router Netgear

Thanks for reading.

---

### Post by patryk77 on 2011-04-01
Might I ask why you would use 2 wireless routers?

And will they be connected to the switch, or do you want them to be entirely wireless?

Entirely wireless would require the router (linux) to be connected to the wireless routers over wifi. The problem I see with that is, you can only associate with one access point, and doubt you could get the two routers to play nice and share the same network SSID.

Having them connected via ethernet would be much simpler if possible; simply assign them two different SSIDs and you'll be all set.

Also, setting up a router to use Wifi as the WAN may be impossible, but if you disable DHCP in the routers and simply configure DHCP on the Ubuntu router or use static IP addresses, it should be feasible.

---

