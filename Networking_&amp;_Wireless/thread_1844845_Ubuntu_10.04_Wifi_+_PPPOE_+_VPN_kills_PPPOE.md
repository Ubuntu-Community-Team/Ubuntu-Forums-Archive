---
title: "Ubuntu 10.04: Wifi + PPPOE + VPN kills PPPOE"
date: 2011-09-15
forum: Networking &amp; Wireless
---

### Post by WorldsEndless on 2011-09-15
I didn't see answers to this exact problem, which is hopefully something fairly simple. I am currently in China and my ISP provided a PPPOE connection for us; using pppoeconfig I have that up and running fine over my wifi. I also purchased a VPN to get around the Great Firewall; I can get it running fully functionally on my Windows XP partition in conjunction with the PPPOE and Wifi connection, and I also work fine from my Ubuntu when working off a normal wifi network; however, when I try to connect here at home after connecting to the PPPOE network, connecting to the VPN causes my PPPOE connection (and therefore all my internet, including the VPN itself) to crash, and I need to re-run "pon dsl-provider" to regain connectivity. I'm no network guru, but I suspect this is just some conflict between how the pppoe manager and the VPN manager are juggling my network settings? 

Once again, the question is how to get VPN + PPPOE to work simultaneously over wifi in Ubuntu 10.04. 

Thanks in advance for any help in getting these to work simultaneously! I absolutely hate voyaging back into Windows just because something won't work in Ubuntu.

---

### Post by duffmansky on 2012-11-24
I have the exact same problem. It is really frustrating that nobody here even attempts an answer in more than a year. I am using 12.04. 
-Connect to wireless first (no it is not possible to connect to adsl on the modem/router, it is locked by the phone company)
-connect to internet with PPPOE (this took a long time to figure out)
-connect to any VPN, PPTP, Ipsec, whatever, in NM says connected. Result is PPPOE connection killed and no VPN. 

ANYONE OUT THERE WITH EVEN A SUGGESTION?

There must be a way to make it work. Buying a router is not an option since I use this setup at multiple places and can't haul a router around with me.

Thanks for any help.

---

