---
title: "Wake on LAN working locally but not over the internet."
date: 2011-08-13
forum: Networking &amp; Wireless
---

### Post by Matt Pellegrini on 2011-08-13
I have got wakeonlan to work locally, waking up my desktop from my laptop by using wakeonlan <mac addr of Desktop> from the laptop. However when i come to do this remotely from a different network over the Internet i can't get it to work.

I use wakeonlan -i mydyndns.com <mac addr of Desktop>
to which i get:
Sending magic packet to mydyndns.com:9 with 00:11:22:33:44:55     <-- mac addr of Desktop
but the machine doesn't actually turn on.

Note that i can ssh to the machine if it is already on so the dyndns stuff is fine.

I have forwarded port 9 to the machine i want to wake up from the router. - this is a step i wasn't sure i needed to do.

So i'm looking for any suggestions to get this to work.
I'm fairly new to all this networking stuff but i've managed to get a lot working quickly so hopefully i can get this working too. Thanks. Matt

---

### Post by drevicko on 2011-08-17
Do you have a firewall running on your router? Is it's packet filter blocking port 9?

I've the same situation: ssh works, wol works from behind the router, port 9 forwarded, packet filter allowing port 9, but no bananas ):

I also tried setting the router firewall to block port 9, tried a wol from a machine in the wider internet and had a look at the firewall log - it didn't block anything. 

My conclusion is that either the machine on the internet is behind a firewall blocking port 9 (I have no control over that, but would like to know how to test it..) or we're doing something wrong with the 'wakeonlan' command.

---

### Post by Matt Pellegrini on 2011-08-19
Thing is port 9 doesn't need to be set to forward to the server machine if you wake it locally. In fact the fowarding is pointless isn't it? The hibernated server doesn't actually have an IP address until it boots up, that's why WOL uses mac addresses. But with port 9 forwarded and without WOL only works locally (machines all connected to the same router) and not over the internet. I'm stuck with this and I've tried a lot I'm sure some one out there has done this and got it to succeed.

---

