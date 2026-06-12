---
title: "Static Internal IP"
date: 2011-01-08
forum: Networking &amp; Wireless
---

### Post by KdotJ on 2011-01-08
Today I bought a new router as my old one had died, it was all a bit of a rush as it just crapped out on me so I needed another to replace it. However, unlike my old router, my new one does not seem to allow me to reserve internal IP addresses on the LAN and just uses DHCP. It does allow port forwarding though...

I have a server, running Debian, and for obvious reasons I need it's internal IP to be fixed. The router, like most, assigns IP addresses within a certain range (let's say xx.xx.0.2 to xx.xx.0.255) and I have the ability to adjust this range to my liking.

Is it possible (or practical) to make my server always connect at say xx.xx.0.2 by configuring the needed file on the server (interfaces i think?) and then just adjust my router to use the range xx.xx.0.3 to xx.xx.0.255 for DHCP for all other devices that may connect?

I hope tat makes sense lol, 
thanks in advance.

---

### Post by PatchesTheCaveman on 2011-01-09
Yeah, that usually works just fine on home networks.

---

### Post by KdotJ on 2011-01-09
Thanks for the reply, I'll give it a try :-)

---

### Post by chili555 on 2011-01-09
> just adjust my router to use the range xx.xx.0.3 to xx.xx.0.255 for DHCP for all other devices that may connect?Is that really what you want to do? Do you really expect 250 (!!!) guests??

Instead, I'd set the router to hand out DHCP addresses from xx.0.2 to xx.0.10 and then set the server's static address to xx.0.20.

I don't think xx.0.255 is valid in any case.

---

### Post by KdotJ on 2011-01-09
Lol no I'm not expecting that many, and the numbers were purely made up in this case. I was just trying to get the idea across with the server being outside the bounds of the assignment range. Thank you for your suggestion, thants the kind of setup I will opt for

---

### Post by PatchesTheCaveman on 2011-01-09
> Is that really what you want to do? Do you really expect 250 (!!!) guests??

I don't see how having a few extra hurts anything.  I know eight is definitely too small for my network, thanks to all the smartphones, e-readers, game systems, televisions, and other sundry devices that support wireless networking these days.

> I don't think xx.0.255 is valid in any case.

Correct.  That's the [broadcast address](http://en.wikipedia.org/wiki/Broadcast_address) for that particular network.  I think DHCPd automatically skips those though so large pools of addresses can be configured more easily.

---

