---
title: "Can an unmanaged switch be used to create a dmz"
date: 2012-12-03
forum: Networking &amp; Wireless
---

### Post by mushy365 on 2012-12-03
Hi, i have a home network. (4 Computers) I'm looking to add a server which will be in a dmz and a NAS
 
So at the minute my modem/router/dns/dhcp/nat is an all in one thing. 
 
I have all 4 pc's connected to it. 
If i was to buy an unmanaged switch, and have this setup
 
<Internet> ---- [modem/router/dns/dhcp] -------- computer 1
###########################---------Computer 2
###########################---------Computer 3
###########################---------computer 4
###########################--------------------------switch-----------server
 
Would this automaticly make the server be in a dmz i.e unable to interact with the other compuers as its through a switch? 
 
Also do you login to switches like you do to a router? does a switch have an ip?

---

### Post by cwsnyder on 2012-12-03
> **mushy365 said:**
> Hi, i have a home network. (4 Computers) I'm looking to add a server which will be in a dmz and a NAS
 
So at the minute my modem/router/dns/dhcp/nat is an all in one thing. 
 
I have all 4 pc's connected to it. 
If i was to buy an unmanaged switch, and have this setup
 
<Internet> ---- [modem/router/dns/dhcp] -------- computer 1
###########################---------Computer 2
###########################---------Computer 3
###########################---------computer 4
###########################--------------------------switch-----------server
 
Would this automaticly make the server be in a dmz i.e unable to interact with the other compuers as its through a switch? Actually, the way I understand a DMZ, the DMZ should be between your Internet connection and your firewall/router.
> **mushy365 said:**
> Also do you login to switches like you do to a router? does a switch have an ip?A straight switch does not have any computer or IP address, it strictly acts as a physical connection between segments of a network.

---

### Post by mushy365 on 2012-12-03
Umm, i'm screwed then. As my router is built in with my modem, etc
also if you had 
 
--[internet] ---- [modem] ------[switch]------[router]-------local network
#######################\
########################\
#########################\
########################DMZ
 
How would you set your gateway etc, since all my dhcp, router, nat, modem etc are all one. Does the gateway ip refer to the modem ip or the router ip?

---

### Post by mushy365 on 2012-12-03
Also, if the above setup is correct, how would the dmz get an ip address. Isnt it the router that is ment to assign local ips?

---

### Post by Cheesehead on 2012-12-03
The drawing you have has *two* local networks. One based on the modem, and including the DMZ and the router. The second is based on the router.
This means the modem must also function as a router.

'gateway' for the LAN would refer to the router. It's their gateway.
'gateway' for the DMZ would refer to it's router (which would be a feature the modem must provide in this case)

However, I think you have made the problem a lot tougher than it needs to be.
If your router has a 'DMZ' feature for a port, then use it for the server. You can always put some of the LAN clients together on the switch.

Modem/Router -----DMZ Port----- Server
##########\
###########\-------Computer 1, Computer 2
############\------Switch --- Computer 3
#####################\--- Computer 4

---

### Post by mushy365 on 2012-12-04
Router does have dmz, i was just wondering if a switch can basically be used to do the same job in my current setup. 
 
I guess the answer is no, i know its a stupid question if i can use my router to do it, but im just trying to understand how it works.

---

### Post by cwsnyder on 2012-12-05
Basically, a DMZ is connected to the wider network (usually the Internet), possibly through a router or firewall, but is separated by a firewall from the rest of your local network to prevent attacks on the servers in the DMZ from spilling over into the resources of the rest of the network.  Also, resources from servers in the DMZ can be made available without making the protected resources visible on the Internet.

Is that any clearer?

---

