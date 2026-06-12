---
title: "Setting a Small LAN to share Internet"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by debraye on 2009-11-20
Hi there, this is my first post arround here so be easy on me, Here is my problem:

I need to share internet and files to a couple of computers, i had already set that up with
a wireless dongle bridged to a ethernet card, but that answer only worked for me to share it to another computer. Now i have an Airport Wireless modem connected to my Internet Router and is currently serving as a DHCP server also, and it all works fine, any computer connected to the Airport via Ethernet, has internet. But, i need to set up one of the computers as a DHCP server and i have no idea how to do that, and keep the internet connection shared between computers. 

so to sum things up, from outer to inner. 2Wire modem connected wireless to Airport, and to the Airport there are other 3 computers connected via Ethernet, one of those computers has to be the DHCP server. I already know how to trick the Airport to stop its DHCP service, but i dont know how to set up the DHCP server in the computer to share the internet connection... I hope i made myself clear, i think im writing in circles.. :D

If there is anything else you guys need to know, feel free to ask, ill be watching this post closely

---

### Post by Iowan on 2009-11-20
For a DHCP/DNS server, **dnsmasq** works well for small networks. If I remember, [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") How-To for ICS mentions using **dnsmasq**.

---

### Post by headvampyre@hotmail.co.uk on 2009-11-20
also you could try samba for that coz i think that has dhcp support

---

### Post by debraye on 2009-11-20
Ok, i finally finished reading all the stuff over there. Lets see if i got this correctly

Fist i shut down the DHCP server on the Airport, then i give one of the comptuers an Static IP and  start and configure the DHCP server on that computer, it wont really matter if its DHCP3-server or dnsmask at this point except for the configuration, i give a range of ips to assign to the client computers, and keep the same subnet, and default gateway the Airport was using. 

Here is the question, when the clients try to connect to the default gateway, how will they know how to reach the internet router trough the airport? will the airport redirect the requests ? will the airport redirect other kinds of requests (files, remote desktop, etc..) to the other clients or the server?

---

### Post by headvampyre@hotmail.co.uk on 2009-11-20
the airport should let the clients connect to the server as long as they are configured on the server and you have ip/tcp enabled on airport also make sure you have setup the clients to actually connect to the servers ip and not the airport and try to avoid dhcp on the router as it might interfere with the static ip unless configured on the router

---

### Post by debraye on 2009-11-20
Well then there would be a problem with the static ip, cause i cannot touch the Router and im pretty sure its handling DHCP requests from its subnet, what if i configure the server and the clients on a different subnet from the router?

---

### Post by headvampyre@hotmail.co.uk on 2009-11-20
it might work or you could invest in another access point for the server and run the server through that wirelessly while still being connected to the airport

---

### Post by Iowan on 2009-11-20
Sorry... getting confused between modem and router. Internet comes in on 2-Wire modem - which connects via wireless to Airport (modem or router?). 3 other computers are wired to Airport. 

One computer can be set as DHCP server with static address. Part of it's job is to tell other clients the gateway address (presumably the static address of the Airport). Which one is the untouchable router that can't have DHCP disabled?

---

### Post by debraye on 2009-11-20
> **Iowan said:**
> Sorry... getting confused between modem and router. Internet comes in on 2-Wire modem - which connects via wireless to Airport (modem or router?). 3 other computers are wired to Airport. 

One computer can be set as DHCP server with static address. Part of it's job is to tell other clients the gateway address (presumably the static address of the Airport). Which one is the untouchable router that can't have DHCP disabled?


The untoucheable is the 2wire router

---

### Post by Iowan on 2009-11-20
OK... Though not exactly true, call the Airport's connection to the 2-wire  the external port, and the "other" port the internal  so the Airport can still get an (external)address from the 2-wire. The "internal (Air)port can be fixed address(?) - preferably different subnet than the external. One of the other boxes can be DHCP server and issue addresses in the "internal" subnet - and pass the Airport's "internal" address as gateway. 

Unless I missed something vital...

---

### Post by bab1 on 2009-11-21
> **Iowan said:**
> OK... Though not exactly true, call the Airport's connection to the 2-wire  the external port, and the "other" port the internal  so the Airport can still get an (external)address from the 2-wire. The "internal (Air)port can be fixed address(?) - preferably different subnet than the external. One of the other boxes can be DHCP server and issue addresses in the "internal" subnet - and pass the Airport's "internal" address as gateway. 

Unless I missed something vital...

If I may add a few cents worth of ideas...

If the 2wire is not available to directly connect via ethernet,  that is a shame.  This will always be a bottleneck for internet speed.

Consider also that if the 2wire is part of the external WAN infrastructure then it is NOT the default gateway.  No more so than the ISP's router that is servicing the subnet that any external interface is on.  It is an extra hop though.

The wireless connection between the 2wire and the external side of the Airport should be on the subnet that is determined by the 2wire.  This is NOT the same subnet as the LAN side network of the 3 computers.  In essence this is the same as the ISP providing DHCP to external side of any home network.

The LAN side of the airport is where the three computers are connected to.  This subnet should be different from the 2wire side of Airport.  

The IP address of the Airport the one that you use to configure the device.  This address is in the LAN side subnet.  This IP address is THE DEFAULT GATEWAY for the 3 computers to use.  One could say; *the default gateway is always the near side IP address of the router the LAN is attached to*.

When we are talking about about LAN communications we are not really using IP addresses other than to be in the same subnet range.  This is all layer 2 so we ARP for the MAC address to communicate.  The 3 ethernet ports are really a builtin Layer 2 switch.  

The Airport serves the function of isolating the LAN from the WAN by communicating back and forth between the 2 different subnets i.e. Internetworking!

So...Configure the LAN side IP subnet to be different from the WAN side.  Give the Airport LAN side a new IP address.  You can now run DHCP there or on any of the 3 computers in the LAN.

---

