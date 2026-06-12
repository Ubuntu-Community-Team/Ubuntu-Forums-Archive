---
title: "Problem accessing the internet with wireless 2200bg and orange livebox router"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by SummerVocal on 2009-01-22
Hi all

I've stumbled upon a strange issue yesterday installing ubuntu on a friend's ACER laptop : I could connect to the wireless router (Orange LiveBox) using wifi but still I couldn't access the internet.

I've done the pairing using the pairing button on the router, typed in the WEP key, and then the signal bars were up in the tray, acknowledging a powerful signal. Nevertheless, no web still.

Oddly, informations about the connection are these :

IP address 192.168.128.12
default route 192.168.128.1
DNS 192.168.128.1

But this address range isn't normally in the range allowed by the router's DHCP server.
Moreover, the DNS and gateway addresses are usually 192.168.1.1, so I think it's this stupid address allocation that prevents me from going out on the internet.

So what can I do to let the roaming profile allow me to use the right addresses ? I've turned to manual mode but then I lose the signal bars in the tray, replaced by the wired one, and the web wasn't reachable either.

Please help ! :)

---

### Post by SummerVocal on 2009-01-22
up!

---

### Post by superprash2003 on 2009-01-22
choose DHCP under your interface options in network manager..

---

