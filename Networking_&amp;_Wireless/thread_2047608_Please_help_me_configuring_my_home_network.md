---
title: "Please help me configuring my home network"
date: 2012-08-25
forum: Networking &amp; Wireless
---

### Post by djevlen on 2012-08-25
Hi all..

So i have little home network as shown on the picture..
I know how to build everything, but i have no idea about IPs/gateways/subnetmasks and so on..

Please help and show me the right configuration for the modem and wireless router.

Right now my pc#s have ip's like 10.0.0.x but thats clas A network..
internet modem has 192.168.1.1 and its assigning ip to the server and to the wireles router.. wireles router is dhcp server for everything connected to the switch. 
there are about 14 network devices on the network connected to switch. The server has 2 nics..one of them i used only for VPN connection so i want it to be connected directly to the modem, and the onther nic is for lan only.

So i just want to know the optimal configuration for my network. the correct ip ranges and correct subnet mask for wireless router and modem. How would this network look like if an network expert would configure it ? :D

thanx

---

### Post by Kirk Schnable on 2012-08-25
Why have the router behind the DSL modem?  The DSL modem looks like it will already do routing things for you.  On a small network of this scale, 2 routers is unnecessary and only adds failure points and latency. 

You already have a switch, so why not just plug that straight into the modem and then everything into the switch?  That topology makes much more sense to me than what you're doing...

Kirk

---

### Post by Bucky Ball on 2012-08-25
+1. Presuming it's a modem/router, scratch the second router. ;)

---

### Post by djevlen on 2012-08-25
> **Kirk Schnable said:**
> Why have the router behind the DSL modem?  The DSL modem looks like it will already do routing things for you.  On a small network of this scale, 2 routers is unnecessary and only adds failure points and latency. 

You already have a switch, so why not just plug that straight into the modem and then everything into the switch?  That topology makes much more sense to me than what you're doing...

Kirk

Because the other router has Wireless and many firewall/blocking options.

---

### Post by Morbius1 on 2012-08-25
Just to clarify:

[1] Is the wireless router in bridge mode and wired: Wireless Router Lan Port to DSL Modem/Router Lan Port. So it's basically a Wireless Access Point?

[2] Or is the Wireless Router Cascaded: Wireless Router WAN Port to DSL Modem/Router Lan Port?

[3] OR is it wired like [1] but not in bridge mode?

---

### Post by djevlen on 2012-08-25
> **Morbius1 said:**
> Just to clarify:

[1] Is the wireless router in bridge mode and wired: Wireless Router Lan Port to DSL Modem/Router Lan Port. So it's basically a Wireless Access Point?

[2] Or is the Wireless Router Cascaded: Wireless Router WAN Port to DSL Modem/Router Lan Port?

[3] OR is it wired like [1] but not in bridge mode?


Its  :  [2]  Wireless Router WAN Port to DSL Modem/Router Lan Port.

---

### Post by steeldriver on 2012-08-25
Mobius' option [1]  is the simplest way to do it imo - just chain the wireless box to the modem-router LAN-to-LAN exactly like a switch and configuring it as a dumb WAP - let the modem-router do both routing and DHCP for everything. I used to do that myself when I upgraded to a wired-only modem-router but wanted to re-use my old WRT54GL for wireless access.

---

### Post by Morbius1 on 2012-08-25
I guess it depends on what you are trying to achieve.

Cascading routers ( item [2] ) is done specifically to create 2 different subnets and / or to make the Moden / Router think there are only 2 dhcp clients - the other router and the server on nic1.

To anyone connected to the wireless router ( the switch, all of it's 14 clients, and the server connecting through nic2 ) it's ip address will be in the 10.0.0.xxx range. The wireless modem's WAN side address will be in the 192.168.1.xxx range consistent with it being a client of the DHCP server of the first router but that has no impact on the second routers DHCP server functions. So to it's clients the ip addresses, gateway, and subnet mask should be consistent with the wireless routers dhcp server.

Anyone connecting directly to the Modem / Router like the server on nic1 will be in a different subnet so things like Samba share browsing will no longer function properly but that may be what you want. Since the server in this case is also connected to the 2nd router via nic2 it should work but to be honest I have done router cascading before but never with 2 different nics pointing to 2 different routers on the same machine.

---

### Post by Bucky Ball on 2012-08-25
Think it should be LAN to LAN. I did the same with a couple of routers for ages. The modem is getting WAN already (presuming the cable for ethernet is plugged directly into modem?) so you just plug the wireless router in like any other LAN device. The WAN/LAN light should start flashing on the wireless router.

---

### Post by djevlen on 2012-08-25
Hmm...

Now i have thrown the wireless router away, and switch is directly connected to the modem-router..

What happened is that transfer rates from server to desktop pc rised to 100MB+ per second which is nice :) although i think it should be the same with the old configuration..but it is not.. strange. THere must have been some conflict in the first network setup..

Anyway..thanx for the advices :)
Ubuntu forums is very helpfull for newbies :D :popcorn:):P

---

