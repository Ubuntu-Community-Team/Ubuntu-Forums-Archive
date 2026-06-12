---
title: "iodone not working unless iptables firewall turned off"
date: 2010-09-28
forum: Networking &amp; Wireless
---

### Post by thejipster on 2010-09-28
I have managed to get iodine working between my ubuntu intrepid box and my windows client with a caveat.

The firewall rules allows DNS queries inbound.
The client tunnel endpoint gets assigned an IP address and the tunnel is established properly.

However when I try to ping from the client machine, the reply packets are not coming back.

I used TCPDUMP on the Ubuntu box and watch the dns0 tunnel interface, and noticed that the packets are reaching the Ubuntu box from the client, but I don't see ANY ICMP echo replies until I turn off the firewall from Firestarter.

I see that outbound access rule is to allow all.

Anyone know why this is happening?


Thanks

---

### Post by kreggz on 2010-09-29
Maybe post the ruleset here if you don't mind

sudo iptables -L

---

