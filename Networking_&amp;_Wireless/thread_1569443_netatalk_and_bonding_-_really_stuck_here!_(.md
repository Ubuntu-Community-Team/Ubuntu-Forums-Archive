---
title: "netatalk and bonding - really stuck here! :("
date: 2010-09-06
forum: Networking &amp; Wireless
---

### Post by wall_e on 2010-09-06
Hi guys,

I've been scouring the internet four about 48 hours in order to get my ubuntu 10.04 server to play nicely with netatalk and a bonded gigabit interface (2 x gbit NICs using ifenslave mode=0).

My switch is a procurve 2650 switch using a static trunk on both gigabit ports.

I'm also using the avahi service to advertise shares to my Mac network.

The aim here is to provide more bandwidth to my network of 10 Mac's.

At present I'm pretty confident my bonded interface is talking to the switch properly because I can see the netatalk service advertised on client machines. Likewise If I stop the avahi-daemon then the bonjour icon disappears in the Mac Finder. Similarly if I update the avahi broadcast name it refreshes in the Finder client side.

The problem happens when I try to connect to the share - in short nothing happens.

If I remove the bonded interface and run  on a single gigabit connection, all is fine :s

Does anybody know how to achieve bonding/link aggregation with netatalk?

I've been over their documentation 10 times and have come to assume that it broadcasts on all available interfaces. Can anybody confirm this? There is an interfaces tag for the atalk.conf but this seems to only relate to AppleTalk services - and I don't have use for apple talk since my Macs are all 10.6. AFP is the aim here.

Cheers in advance.

---

