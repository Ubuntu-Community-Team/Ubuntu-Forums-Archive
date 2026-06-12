---
title: "Adding a wireless access point"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by Josh1 on 2009-09-14
Hey all,
I desperately need to add a wireless access point to the network to add wireless functionality as the card I don't want to use AD-HOC for a wireless card.

My situation is like this:

((INTERNET)) <--> [MODEM] <-ETH1-> <<SERVER>> <-ETH0-> [[SWITCH]] <--> COMPUTERS

I'm going to probably buy [this]("http://austin.net.au/ProductList/tabid/103/Search/1/Keyword/access%20point/Default.aspx"), would I just plug it into the network, configure it (disable DHCP as the server would pass DHCP/NAT)?

Thanks.

---

### Post by p1t0u on 2009-09-15
Basically yes, think of the wireless access point as just another switch.  If you needed more ports
than provided by your current switch you could just add another and hook them up together.  Same
thing with the WAP except you have to configure security on it so you can control who is allowed to 
connect.

---

