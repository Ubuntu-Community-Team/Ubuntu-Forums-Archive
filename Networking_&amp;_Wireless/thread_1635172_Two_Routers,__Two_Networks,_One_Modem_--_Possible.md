---
title: "Two Routers,  Two Networks, One Modem -- Possible?"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by funnysnoot on 2010-12-01
I have a unique problem that I've not yet found a solution to, so I thought I'd ask here.

I have a cable modem that is connected to a standard router with all ports being used. Now, because of certain circumstances, I need to add a wireless router and create an entirely new network, using the same modem (keeping the other network intact).

My thought was to purchase a wireless router and an ethernet splitter, and split the connection coming from the modem, but I'm not entirely sure if this is possible. Has anyone attempted anything like this before? Would there be another way to go about doing this?

Any suggestions or comments would be appreciated. Thanks.

---

### Post by endotherm on 2010-12-01
my advice is instead of gettting a wifi router, get a wifi Access point, or a router that can act as a router/bridge/AP all in one. 
if you do get a second router, and cannot configure it as an AP, then connect the wifi routers wan to the lan of the other router. you will end up with two networks, but you would anyway, unless you use an AP. 
there isn't really such a thing as an ethernet splitter, but there are plenty of Hubs/switches that woudl do the job, but I don't think you can directly connect a switch to a cable modem. I believe you need the first device off the line to be a router or a end-system.

---

### Post by SeijiSensei on 2010-12-01
> **funnysnoot said:**
> My thought was to purchase a wireless router and an ethernet splitter, and split the connection coming from the modem, but I'm not entirely sure if this is possible. Has anyone attempted anything like this before? Would there be another way to go about doing this?

Configure the wireless router's DHCP server to distribute addresses in a different network block than the one your current router uses now.  Then plug the wireless router's WAN port into one of the ports on your current router.  It should get an address from that device.  If all goes well, machines connected to the wireless router should be able to browse the Internet and the wired local network directly.

Things get tricky if you have to connect directly to machines behind the wireless router, but that's pretty unlikely in most applications.  Just put any servers or other shared resources on the wired network and use the wireless only for client machines.

---

### Post by funnysnoot on 2010-12-01
Thanks for your input, endotherm.

So, let me see if I understand what you are saying:

I already have the wireless router, so coming from the modem my connection should be chained like this:

Modem --> Wireless Router --> Original Router

I'd plug my ethernet cable from the modem into the wireless router and then plug a cable into a port on my wireless router and connect it into the LAN port on the original router. So, in essence, my internet connection is running through the wireless router first.

Does that make sense?

Thanks.

---

### Post by funnysnoot on 2010-12-01
Thanks, SeijiSensei. What you're saying makes sense, but if I understand what you're saying correctly, it won't work for my situation. The network that exists now, must exist as it does, and cannot be browsed by any other machine not on the network. So, this new wireless network I want to setup will contain devices that cannot and should not be able to browse devices on the existing wired network.

This is where I think it gets tricky unfortunately. Thanks for your reply.

---

### Post by endotherm on 2010-12-01
> **funnysnoot said:**
> Thanks for your input, endotherm.

So, let me see if I understand what you are saying:

I already have the wireless router, so coming from the modem my connection should be chained like this:

Modem --> Wireless Router --> Original Router

I'd plug my ethernet cable from the modem into the wireless router and then plug a cable into a port on my wireless router and connect it into the LAN port on the original router. So, in essence, my internet connection is running through the wireless router first.

Does that make sense?

Thanks.

yeah, that will work, but it has the side effect of requireing you to have two networks, one for wireless and one for wired. wired hosts will be able to access wifi network resources, but the wifi clients will probably not be able to access services and resources on the wired network.  
see if you can get your wifi router to work in AP mode. if so, the AP will just add wireless to your existing wired lan, rather than adding a second network (simply put, where ever you have a router, you have a new network).

then wire it like this:
Modem -> Router -> WifiAP

that is my best recomendation, if you have specific criteria for wifi security however, your approach may be better. all depends on whether the wifi clients will ever need stuff on the wired network.

---

### Post by SeijiSensei on 2010-12-01
> **funnysnoot said:**
> Thanks, SeijiSensei. What you're saying makes sense, but if I understand what you're saying correctly, it won't work for my situation. The network that exists now, must exist as it does, and cannot be browsed by any other machine not on the network. So, this new wireless network I want to setup will contain devices that cannot and should not be able to browse devices on the existing wired network.

If you can create firewalling rules on the existing router, just add one that denies access to the existing network from the wireless router's address.  Since it will be masquerading as all the machines behind it, that effectively blocks access from any of the wireless clients.  Make sure you permit access from the wireless router's IP to the rest of the Internet, of course.

---

### Post by funnysnoot on 2010-12-02
Thanks to both of you for your advice. Much appreciated.

---

