---
title: "need to make a TCP/IP network"
date: 2012-02-05
forum: Networking &amp; Wireless
---

### Post by Blochee on 2012-02-05
Hi.  I'd like to set up a network of about 5 or more computers to play Netmaze using Ubuntu.  To my knowledge Netmaze requires a TCP/IP network.  Is this any different from a LAN network?  Will I need a router?  How should I proceed?

Thanks in advance!
Blochee

---

### Post by helgman on 2012-02-05
> **Blochee said:**
> I'd like to set up a network of about 5 or more computers to play Netmaze using Ubuntu.  To my knowledge Netmaze requires a TCP/IP network.  Is this any different from a LAN network?  Will I need a router?  How should I proceed?

To answer the most pressing question, a "LAN" is a [Local Area Network]("http://en.wikipedia.org/wiki/Local_area_network"). If the computeras are close to one another you can interconnect them via a LAN. The LAN is just the most basic technology that makes sure that the computers can send data to one another.

To get the game (?) going you'll need some extra networking ontop of the LAN. The most common protocols used with Ubuntu (no, no source, just a guess) is [TCP/IP]("http://en.wikipedia.org/wiki/Tcp/ip"). TCP/IP should run without any problems ontop of most LANs. That's a basic concept in computer networks, "[layering]("http://en.wikipedia.org/wiki/Abstraction_layer")". By layering, it's possible to use TCP/IP on top of a network infrastructure using copper wire, raido waves or optical fiber. Isn't that nice?

If all the computers are connected to the same LAN, you won't need a router. Just make sure the computers are in the same ([IP]("http://en.wikipedia.org/wiki/Internet_Protocol")) [subnet]("http://en.wikipedia.org/wiki/Subnetwork") and you'll be fine. Don't get confues by the fact that it's called "the internet protocol" ... you can use it without bothering with the Internet.

If the computers are spread across the Internet (or intranet) (not on the same LAN), then you'll need a router, proboly an [ISP]("http://en.wikipedia.org/wiki/ISP") or [NSP]("http://en.wikipedia.org/wiki/Network_Service_Provider") or some IT staffer that can make sure that the computers are able to communicate ... but from you post, it looks like you're going for the LAN, right?

I hope I answerd your questions. If not, keep asking ... if I'm not around someone else might be.

Regards,
Helgman

---

### Post by SeijiSensei on 2012-02-05
> **Blochee said:**
> Will I need a router?  How should I proceed?

If you're willing to configure each computer manually, then you can simply buy an [eight-port "switch"]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833166035") into which all the computer will be connected.  Each computer would need its TCP/IP configuration set manually, with all the computers in the same "subnet."  The addresses from 192.168.0.0 through 192.168.255.255 have been set aside for private networks without a need to connect over the public Internet.  So you could assign the first machine to 192.168.10.1, for instance, then use 192.168.10.2, etc., for the remaining machines.

A router would simplify this process considerably since you can then let the machines request their configuration information from the router via the standard "Dynamic Host Configuration Protocol" or "DHCP".  A router would also enable you to have these computer reach the Internet if you would like.  

If you don't need wireless, this [eight-port router]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833704070") looks like a good bet.  If you can't find a router you like with eight ports, you can plug a four- or eight-port switch into one of the router ports to create more available connections.

---

### Post by haqking on 2012-02-05
> **Blochee said:**
> Hi.  I'd like to set up a network of about 5 or more computers to play Netmaze using Ubuntu.  To my knowledge Netmaze requires a TCP/IP network.  Is this any different from a LAN network?  Will I need a router?  How should I proceed?

Thanks in advance!
Blochee

TCP/IP is a suite of protocols (hundreds or so) and its how computers talk to each other, it is a universal language so different networking hardware can talk to each other.

Pretty much every LAN and WAN now uses TCP/IP by default, and certainly Linux/Ubuntu does so its there by default, you just might need to configure things.

Cheers

---

