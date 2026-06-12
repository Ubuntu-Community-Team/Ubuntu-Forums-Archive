---
title: "Dual Internet Connection Headaches"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by sl4ck3r on 2011-01-18
Hey there guys.  I've got both a cable and DSL connection set up in my  house. I've got Ubuntu Server 10.10 running and am using Shorewall to do all  the configuring.  I've got things set up as follows:  

- eth0 (my LAN) 
- eth1  (Cable) 
- eth2/ppp0 (DSL/Primary Connection)  

I've got things routing  just fine, I am forcing all traffic from my LAN to my DSL connection  (even though I've specified track,balance in my providers file).  The  headache comes from I want 2 of my computers on my LAN forced over to my  cable connection and it seems that my system is just not having it.   Here is what my route_rules file looks like:

> 
[FONT=Courier New]#SOURCE              DEST    PROVIDER           PRIORITY
192.168.0.20    -          Distributel     11999
eth0                    -          MNSi                   11999[/FONT]


When I remove the first line from route_rules everything works as it should, when I put it back, the computer at address 192.168.0.20 can't connect out to anything. I've verified that the connection is working and I'm getting DHCP (I'm getting dropped packets from various IP addresses from eth1 in my log file). 

I've tried using Googles DNS servers in case it was a DNS issue but it is not.

I'm not really sure where to go from here. 

Help? ](*,)

---

### Post by mips on 2011-01-19
Provide configs from all machines in the network as well as output of traceroutes & ping.

A little diagram of the network would also help in visiualising your setup.

---

### Post by sl4ck3r on 2011-01-19
> **mips said:**
> Provide configs from all machines in the network as well as output of traceroutes & ping.

A little diagram of the network would also help in visiualising your setup.

Here's a diagram of how I have things set up. The 2 switches are used to minimize the cabling needed throughout the house.

What traceroutes/pings are you looking for exactly?

[IMG]http://www.tunasandwich.net/images/ubuntuforum/network%20diagram.png[/IMG]

---

