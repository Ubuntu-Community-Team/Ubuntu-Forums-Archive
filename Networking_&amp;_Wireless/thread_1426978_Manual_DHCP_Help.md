---
title: "Manual DHCP Help"
date: 2010-03-10
forum: Networking &amp; Wireless
---

### Post by Kvothe on 2010-03-10
One of the routers that I connect to regularly suddenly stopped sending out DHCP info. I am able to connect with my Nintendo DS using the IP, Subnetmask, Gateway and DNS server values that I obtained earlier, but I cannot figure out how to do so on my Ubuntu laptop ( [9.10 Karmic Koala] x86 64-bit ). I need to know what to put in for each value on the manual DCHP GUI, specifically the Search Domains field and the "Routes..." dialog. A response before tomorrow would be especially appreciated.

---

### Post by dmizer on 2010-03-11
> **Kvothe said:**
> One of the routers that I connect to regularly suddenly stopped sending out DHCP info. I am able to connect with my Nintendo DS using the IP, Subnetmask, Gateway and DNS server values that I obtained earlier, but I cannot figure out how to do so on my Ubuntu laptop ( [9.10 Karmic Koala] x86 64-bit ). I need to know what to put in for each value on the manual DCHP GUI, specifically the Search Domains field and the "Routes..." dialog. A response before tomorrow would be especially appreciated.

I highly suggest rebooting the router, as this may repair the DHCP server.

The "Search Domains" field is for your DNS servers. More information on the "Routes ..." dialogue here: [http://en.wikipedia.org/wiki/Static_routing](http://en.wikipedia.org/wiki/Static_routing)

---

### Post by Kvothe on 2010-03-11
> **dmizer said:**
> I highly suggest rebooting the router, as this may repair the DHCP server.

The "Search Domains" field is for your DNS servers. More information on the "Routes ..." dialogue here: [http://en.wikipedia.org/wiki/Static_routing](http://en.wikipedia.org/wiki/Static_routing)
I do not have direct access to the router itself, though I suppose I could ask them to do it (after finding the appropriate staff member).

Thanks, but do I need to use both the "DNS Servers" and "Search Domains" fields? And is the "Routes ..." information needed, and how does it differ from the values in the main dialog? What I wanted to know was what is absolutely required to connect, and what values I would need in order to fill those requirements. I am sorry if I did not make that very clear.

---

### Post by Kvothe on 2010-03-11
I still do not have all of the info that I need, and this has gotten pushed back quite a bit. Sorry for the bump, but I do need it soon, and it seems you guys needed a reminder.

---

### Post by dmizer on 2010-03-11
If you need immediate help, you should try something which will provide you with immediate help like IRC: [https://wiki.ubuntu.com/InternetRelayChat](https://wiki.ubuntu.com/InternetRelayChat)

---

### Post by Kvothe on 2010-03-11
Solved. I am sorry to have demanded your time. -_-;

---

