---
title: "sharing a cabled connection (thruogh a linksys access-point)"
date: 2009-09-09
forum: Networking &amp; Wireless
---

### Post by tsr on 2009-09-09
Hi,

I´m sharing an internet-connection with some neighbors and recently the ISP got us a new dsl-modem/router that only gives out 4 ip-adresses. That is obviously too few for our needs.

I also have this linksys wireless access-point that I think should be able to help us out.

My idea is to connect my main-computer through the wireless-nic to the dsl-modem/router and then connect my access-point to my cabled-nic and allow the other computers in my household (3-8, depending on who is here) to connect wirelessly to the linksys and so access the ´real´ internet-connection.

Unfortunately I´m not very skilled at this whole configuring thing and all the howto:s I´ve found talk about internet-sharing the other way around.

Any pointers are welcome but outright step-by-step instructions are extremely appreciated.

/tsr

---

### Post by x22 on 2009-09-11
if I understand your idea, the hookup looks like this:

dsl-modem/router->(wireless)->PC->(cable)->linksys
AP->(wireless)->other machines

the PC would get assigned 1 of the 4 ip-addrs, then
thru port-forwarding pass the other 3 on the the AP:
how is this an advantage?

the AP is not a router--it assigns no ip-addrs, but
accepts them from an upstream router.  A simpler
method would be

dsl-modem/router->(cable)->AP->(wireless)->PC and other
machines

is this a DSL setup?  personally, I have never heard of
an ISP providing anything but a so-called "modem" that
provides a TCP/IP connection to (PC, router, whatever).
Then a router such as linksys wrt54g assigns the
ip-addrs, a hundred or more.

---

