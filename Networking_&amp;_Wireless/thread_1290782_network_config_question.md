---
title: "network config question"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by mfleming on 2009-10-13
I have an ubuntu server that I need to connect to the internet, as a webserver etc. So I have ordered an internet connection from Time Warner with a static IP address. I could set the server to the static IP address assigned to Time Warner's modem, and then away we go.

Except ... I have other devices that also need to connect to the Internet over the cable modem. So I'm thinking I'll have to add a second ethernet card to the server, and connect a switch or router to this. The server will then have to be configured as a gateway for the switch.

I've never done anything like this before and I'd really appreciate a few pointers as to:

1. What kind of router or switch I need. At the moment I have a Linksys cable/DSL router #BEFSR81, but maybe this was a bad choice (at first I thought I could configure all this through the router).

2. How to configure the server to function as a gateway.

Thanks very much!

Matthew Fleming

---

### Post by bab1 on 2009-10-14
> **mfleming said:**
> I have an ubuntu server that I need to connect to the internet, as a webserver etc. So I have ordered an internet connection from Time Warner with a static IP address. I could set the server to the static IP address assigned to Time Warner's modem, and then away we go.

Except ... I have other devices that also need to connect to the Internet over the cable modem. So I'm thinking I'll have to add a second ethernet card to the server, and connect a switch or router to this. The server will then have to be configured as a gateway for the switch.

First I would see if the cable modem can be configure as the gateway, i.e. provide NAT, Firewall and internal DHCP for the private LAN. If so then all you would need is a 4 or 8 port switch.  

If the cable modem does not The I would investigate a SOHO router/switch combo capable of providing what I mentioned above.

It is true that you can do all of this using the Linux server, but why beat yourself up configuring IPTables DNS and DHCP if you don't have to.  SOHO Router/switch combos are common place these days.> 

I've never done anything like this before and I'd really appreciate a few pointers as to:

1. What kind of router or switch I need. At the moment I have a Linksys cable/DSL router #BEFSR81, but maybe this was a bad choice (at first I thought I could configure all this through the router).

The Linksys should work fine in this setup. > 

2. How to configure the server to function as a gateway.I would only do this as a last resort.  I'm not saying you can't, but I would walk (learn the basics) before trying to run.[/QUOTE]

---

### Post by mfleming on 2009-10-14
I don't know about the cable modem, but the Linksys router is designed to connect to a cable modem, and has 8 ports. It provides all of what you mentioned -- internal DHCP, firewall, and NAT. However, I called Linksys tech support and explained the situation. They said that I could set the router to the static IP that Time Warner would provide or I could directly connect my server to the cable modem and give it the static IP. If I connect the server, then I'd have to give it a second ethernet card and configure it as a gateway, as I described. If I connect the modem, then I don't see how I can make the server accessible to the world via the static IP address. 

Maybe I should get some other kind of hardware? Or maybe the Linksys tech people just didn't understand what I was trying to do? If I can avoid having to configure the server I'd certainly prefer to do so.

Matthew

---

### Post by bab1 on 2009-10-14
> **mfleming said:**
> I don't know about the cable modem, but the Linksys router is designed to connect to a cable modem, and has 8 ports.

This is really a router with a switch built  in.  This is all you need to have in the way of hardware.>  

It provides all of what you mentioned -- internal DHCP, firewall, and NAT. 
So far so good.> 

However, I called Linksys tech support and explained the situation. They said that I could set the router to the static IP that Time Warner would provide or I could directly connect my server to the cable modem and give it the static IP. 

If I connect the server, then I'd have to give it a second ethernet card and configure it as a gateway, as I described.
These are still the same two options. > 

If I connect the modem, then I don't see how I can make the server accessible to the world via the static IP address.
This is easily accomplished with Linksys router.  NAT translates the the external (cable supplied) IP address to the internal (private) IP address.  The TCP/IP port identifies which host (machine) in the private network the pubic is trying to reach.  It will help if you read [_**[COLOR="DarkSlateGray"]this[/COLOR]**_]("http://portforward.com/help/portforwarding.htm")> .  Here is [**_[COLOR="DarkSlateGray"]more information[/COLOR]_**.]("http://www.google.com/search?q=port+forwarding+IP&btnG=Go!") 
[QUOTE]
Maybe I should get some other kind of hardware? 
I think what you have is good.  We just need to configure it correctly.> 
Or maybe the Linksys tech people just didn't understand what I was trying to do? 
IMO all first tier help desk are unknowing.  They have a book of common questions and answers.  They did not give you bad info, just not detailed enough.> 
If I can avoid having to configure the server I'd certainly prefer to do so.

i agree and we will configure the Linksys .

---

### Post by mfleming on 2009-10-14
Thank you for your advice. Yes, I had pretty much figured out that I can use port forwarding to do what I want. 

I'm not sure if I have to turn off DHCP completely, and use all static addresses, or just reserve the server's internal address so that it is not assigned by DHCP. Probably I'll be able to do the latter. Then I'll just have to set a static IP address on the server, forward the ports I'm interested in, set the router as the server's default gw, bind my server's DNS name to the cable modem's static IP address, and set resolv.conf on the server to point to Time Warner's DNS servers. My current server uses iptables but I don't think I should need this with port forwarding.

That's pretty much it, isn't it?

Thanks again,

Matthew

---

### Post by bab1 on 2009-10-14
> **mfleming said:**
> Thank you for your advice. Yes, I had pretty much figured out that I can use port forwarding to do what I want. 

I'm not sure if I have to turn off DHCP completely, and use all static addresses, or just reserve the server's internal address so that it is not assigned by DHCP.

Probably I'll be able to do the latter. Then I'll just have to set a static IP address on the server, forward the ports I'm interested in, set the router as the server's default gw, bind my server's DNS name to the cable modem's static IP address, and set resolv.conf on the server to point to Time Warner's DNS servers. My current server uses iptables but I don't think I should need this with port forwarding.

That's pretty much it, isn't it?


Yes indeed!  You are correct that in a small network DHCP is not really needed.  You do not need to reserve a static address.  The pool of DHCP controlled addresses is usually LESS than the total IP addresses in the subnet.  If not, you can reduce the pool size.  Then you can use an address NOT in the pool.  I have DHCP for my laptops and everything else (6 servers/desktops) are manually configured static IP addresses.

IPTables is not needed in this setup.  IPTables is all the routines you would use to duplicate the Linksys device in Linux.  Pretty heavy duty for your needs.

---

### Post by mfleming on 2009-10-14
Thanks again for your help. I would have figured it out sooner except for the misleading information from Linksys (and I spoke to 2 of their technicians, who both said the same thing).

Matthew

---

