---
title: "DHCP client only works when TCPDUMP is enabled"
date: 2013-07-09
forum: Networking &amp; Wireless
---

### Post by mosquetero on 2013-07-09
Hi all,

My Ubuntu DHCP client does not recognize the DHCPOFFER created by the DHCP server unless TCPDUMP is monitoring in the same ethernet interface. I guess that the difference is that when TCPDUMP runs, the network interface is in promiscuous mode and then it accepts all the packets. However, why is it not working when it is not in promiscuous mode? It should recognize its own MAC address and process the packet.

Does anybody experience that before? Any clue about what it is happening?

Thanks

---

### Post by mosquetero on 2013-07-10
Hi!

I solved the problem restarting the switch :P

---

