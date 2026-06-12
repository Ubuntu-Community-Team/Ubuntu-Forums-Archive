---
title: "Help for Network Configuration - Router AFTER IP Switch &gt;&gt;&gt; HowTo?"
date: 2009-01-18
forum: Networking &amp; Wireless
---

### Post by stoynev on 2009-01-18
Hello I need some help for the following network configuration,

Lets say that I have my Router AFTER the IP Switch... >

I got my IP range from ISP(30IPs) - for example router IP should be: 30.40.50.60

Local Network: 10.0.0.0

Thats a example of the network.
ISP FiberOptic -to-> SWITCH -1to-> ROUTER
------------------------------------2to-> Servers (Real/Public IPs)
------------------------------------3to-> Workstations (Local Network)

The problem is that the connection will be Fiber Optic and its going to the switch first., what configuration should I use(for the switch, for the router,for the local computers and the connection between them how should it be).

The hardware is following:

SWITCH: HP Procurve 4208vl-72GS Switch 68 x 10/100/1000 Ports + 4 x mini-GBIC Slots

[IMG]http://images.tigerdirect.com/skuimages/large/H24-J9030A-main.jpg[/IMG]

ROUTER: Mikrotik Routerboard RB1000

[IMG]http://www.roc-noc.com/images/P/rb1000rm.png[/IMG]


Thanks.

---

### Post by diablo75 on 2009-01-19
I might have to bite my lip later...  But I don't really see the need to do anything special here.  You'll run a standard ethernet cable from one of the ports on the switch into the uplink port on the router (just like any old home network router), then hook up your four PCs.  Assuming everything is running DHCP, that is.

---

### Post by stoynev on 2009-01-19
The router should be after the switch and the FiOS is going directly to the switch, so I am wondering the first machine in the network with the first ISP Public IP will be the switch or the router?
In that configuration that I have described up , can I do the router the first public IP machine and the switch with local IP and the connection to go first though the router and after that to the server and then back to switch to distribute to other machines.

Or I need to make the switch with FiOS going in, the first machine in the Public Network and then to give Public IP to the server and with the second LAN of the router to distribute local IPs....,

---

### Post by stoynev on 2009-01-19
I figured it out. Thanks :)))))))

---

