---
title: "Multiple LAN's"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by Amatøren on 2009-09-10
I am working on a ubuntu server. On the mother board I have one LAN port and I hve put in an extra 4 port LAN card. When I checks it looks like al ports has unike MAC adresses (so that is OK). When I setup the network and connects cables to all LAN posts, only on IP address is active (in uses) when I checks my ADSL modem (interface meny). 

When I connect one IP address (that is defined in the interfaces) but not active ref. ADSL modem is the connection routed internal in server by active IP, or is all active but I am confuesd by the ADSL modem interface meny?

My interfaces file:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface (motherboard)
auto eth0
iface eth0 inet static
address 192.195.0.150
netmask 255.255.255.0
network 192.195.0.0
broadcast 192.195.0.255
gateway 192.195.0.138

# The 4 port lan card
auto eth1
iface eth1 inet static
address 192.195.0.151
netmask 255.255.255.0
network 192.195.0.0
broadcast 192.195.0.255
gateway 192.195.0.138

auto eth2
iface eth2 inet static
address 192.195.0.152
netmask 255.255.255.0
network 192.195.0.0
broadcast 192.195.0.255
gateway 192.195.0.138

auto eth3
iface eth3 inet static
address 192.195.0.153
netmask 255.255.255.0
network 192.195.0.0
broadcast 192.195.0.255
gateway 192.195.0.138

auto eth4
iface eth4 inet static
address 192.195.0.154
netmask 255.255.255.0
network 192.195.0.0
broadcast 192.195.0.255
gateway 192.195.0.138


```

I have tested with gateway on only eth0, but no help.

I want each STB and playback PC to connect the server by seperatly IP adresses to prevent to low bandwith on one single LAN (so only server capasity is the limit for streaming and record).

---

### Post by Iowan on 2009-09-10
Having the network cards in the same subnet probably won't work well... without bridging (or some involved iptables rules) - it plays havoc with routing.

---

### Post by Amatøren on 2009-09-14
So it's not possible to have several lan cards with diffrent IP addresse's to let diffrent STB's to access it's own LAN card to increase streaming "speed limit"?

:confused::confused::confused::confused:

---

### Post by Iowan on 2009-09-14
There is some bridging information in [this]("https://help.ubuntu.com/9.04/serverguide/C/network-configuration.html") help page. Maybe it will be of help.

---

### Post by p1t0u on 2009-09-15
> **Amatøren said:**
> So it's not possible to have several lan cards with diffrent IP addresse's to let diffrent STB's to access it's own LAN card to increase streaming "speed limit"?

:confused::confused::confused::confused:

The thing is that IP does not care where the frames came from; it looks at it's routing
table to decide how to send the replies.

If you have a fixed relationship between the clients and the interface you want them to use to connect to the server you would have to set up static routes for all clients specifying which card you want to use to talk to them.  Something like:

route add -host w.x.y.z ethx

where w.x.y.z is the IP address of the client and ethx is the interface to use on the server.

I have not tested this so you may have to refer to "man route" for the proper incantation.

Whether you get increased transfer speeds with multiple cards may depend on the 
capacity of the switch you use.

---

### Post by KiLaHuRtZ on 2009-09-15
I think this is what you are looking for.

[http://www.debianhelp.co.uk/bonding.htm](http://www.debianhelp.co.uk/bonding.htm)

---

### Post by Iowan on 2009-09-15
Hmmm... maybe it was bonding rather than bridging...
[Here]("https://help.ubuntu.com/community/UbuntuLTSP/Trunking") is another one on bonding.

---

### Post by Amatøren on 2009-09-18
My network switch is BayStack 450 24T. I can set up up to 4 ports in a truck for 400 Mb LAN connection. I know by seeking checking the Internet I possible can find anytihing about it, but the quick way: A tip where to find info about setup 4 ports nic to a trunc, please.


Best regards

Amatøren

---

### Post by badger_fruit on 2009-09-18
It looks like from your original post you don't want bridging or bonding; if you want 5 x NICS with 5 different IP addresses as you seem to have set up in your interfaces file.

As far as I know you don't need to set anything other than the appropriate IP Address on each STB.
Example:-

STB 1 --> 192.195.0.150
STB 2 --> 192.195.0.151
STB 3 --> 192.195.0.152
...
STB X --> 192.195.0.xxx

Bonding allows you to use multiple NICS with a SINGLE IP ADDRESS; if configured right can allow good resiliance and load-balancing but not what you seem to be asking.  I also believe that your router/switch needs to support this (although that would need to be confirmed).

Bridging allows a user on Machine 1 to connect to a resource by connecting to Machine 2 on IP 192.195.0.150 and then that bridges to NIC 2 which points to Machine 3. I think!  I'm not certain, google will be able to define this better than I.

If you go to another machine and PING the individual IP addresses of the server, do you get a reply?
if so, what is the problem exactly?




EDIT: Setting up 4 NICS to 1 "TRUCK"
Why? Surely this would REDUCE capacity as each NIC would be forced to use a single socket on your switch?
Each NIC should be connected to their own seperate socket to get the best performance.

Hmm:-

> 
MultiLink Trunking&#8212; Trunking enables your network&#8217;s devices to interpret the virtual geography of the network. This fail-safe function can be implemented across the stack, and connections between individual devices (such as those linking a switch and a routing switch) can be aggregated for both higher bandwidth and redundancy. If one port connection fails, other connections within the trunk seamlessly carry the full traffic load. Your servers and other important resources can be connected to different switches in the stack to achieve multi-homing and extend your link redundancy.


[http://www.blackbox.co.uk/technical/pdf/21755.pdf](http://www.blackbox.co.uk/technical/pdf/21755.pdf)

[http://lmgtfy.com/?q=how+to+set+up+trunk+baystack+450+24t](http://lmgtfy.com/?q=how+to+set+up+trunk+baystack+450+24t)

---

### Post by Amatøren on 2009-09-18
Thanks for repsponce on my post.

It's OK to setup One IP on 4 ports and use them in a trunck for 400Mb connection. I understand now that I was missing some understanding of the previus tip.

My switch is a BayStack 450 24T and I can setup 4 and 4 ports into trunck's to increase the LAN speed up to 400Mb at each IP adress.

So by use the 4 port LAN card (disable the onboard LAN) I can get 400Mb connection to my switch.

Is a trunck what you call bonding?

---

### Post by badger_fruit on 2009-09-18
I don't really know enough about your switch, does it assign an IP to a port or something?
If it does then I guess you can assign 1 IP to 4 ports and use this trunking (which does sound like BONDING).

I would expect that the switch itself may have a single IP to allow remote-management but I'm not sure at all about that.

I made a diagram in MSPaint (attached).

This is how I THINK it would work, obviously, the lines are not physical cables but the virtual cables, defined in your port-management or trunk.

As you see, Switch port 1 has 4 virtual cables, all pointing to NIC 192.195.0.150 and Switch port 2 has again 4 virtual cables pointing to NIC 192.195.0.151.  Naturally, this pattern would continue for the other two NICS in the PC.

This would use 4 switch ports (giving 400mbps) for each NIC - from what I understand (and this is based on pure guesswork lol!)

As for how to set this up, I have no idea at all - suspect there'll be a web-management port on the switch which you'd do this through.

---

