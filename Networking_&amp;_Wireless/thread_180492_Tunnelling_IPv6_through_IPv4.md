---
title: "Tunnelling IPv6 through IPv4"
date: 2006-05-22
forum: Networking &amp; Wireless
---

### Post by spd106 on 2006-05-22
First I realise that the network will be disabled in a few weeks but I wanted to try it out anyway.

Ok, I've set up a connection with a tunnel broker [here]("https://tb.ipv6.btexact.com/"), I'm with BT so there shouldn't be any problems there and the link says it has been configured and I can ping the tunnel brokers address over IPv4.

Some details about my setup: I have a laptop with wifi to a wifi router. The router has an BT voyager modem conected to it through ethernet and to the ISP over ADSL. The modem and router are on one subnet and the internal network are on another. So effectively there are two NAT gateways. 

So, I downloaded the setup script which creates a new sit interface sit1 with the default details. I can ping the sit1 interface no problem (~loopback?). So when it comes to pinging the brokers IPv6 address I get no replys. I'm thinking that the router is stopping the replys.

Looking through the router logs I see an entry saying WAN DoS protection from the broker's IPv4 address. Is this a ping reply?

The broker site says that if you use NAT your equipment must support protocol 41 forwarding or something. I tried putting the laptop in the DMZ but it didn't work. I'm not sure how to set up forwarding. I'm not sure what this protocol 41 is or how to find out. Any ideas?

---

