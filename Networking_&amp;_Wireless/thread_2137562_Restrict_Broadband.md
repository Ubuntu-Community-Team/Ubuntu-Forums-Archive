---
title: "Restrict Broadband"
date: 2013-04-21
forum: Networking &amp; Wireless
---

### Post by Quarkrad on 2013-04-21
I'm running 12.04 on one pc and 12.10 on another - not sure if this is relevant but each have a static ip on my home network (of 2 pcs!).  I'm in the UK and currently have a broadband download speed of approx 6mb.  Is there a way of restricting the bandwidth so either one (preferably both) machines have 2mb?  I've had a look at my router (dlink dsl-2680) but there dosn't seem to be an easy way of restricting the speed.  I was wondering if it could be done at the pc end?

---

### Post by sanderj on 2013-04-21
Limiting inbound ("ingress") is always hard. It's like a French goose trying to refuse food that's fed via a tube ... ;-(

You could have a look at "tc" and examples of limiting ingress traffic. And "man tc", especially: "policing pertains to traffic arriving. Policing thus occurs on ingress."

---

### Post by Quarkrad on 2013-04-21
Thanks.  I found an easy way to do what I was aiming for.  Used something called wondershaper - see:

[http://www.ubuntugeek.com/use-bandwidth-shapers-wondershaper-or-trickle-to-limit-internet-connection-speed.html](http://www.ubuntugeek.com/use-bandwidth-shapers-wondershaper-or-trickle-to-limit-internet-connection-speed.html)


to install sudo aptitude install wondershaper

---

### Post by sanderj on 2013-04-21
So just


sudo wondershaper eth0 10000 280

sudo wondershaper eth1 downspeed upspeed

Note:- Speed should be in KB



... that would be nice!

---

### Post by btindie on 2013-04-21
That's fine if there's just one device on your network, but to do it effectively you need to do the traffic shaping on your edge device, i.e. your router.

Otherwise you'd be restricting each of your computers to only use 2Mb of bandwidth even though more was available. It's even worse if only one of your computers was in use. Whereas by doing it on the edge of your network you can control the bandwidth used by all devices and utilise the maximum available.

Example given at [http://www.mastershaper.org/index.php/Howto](http://www.mastershaper.org/index.php/Howto)

[http://lifehacker.com/326543/ensure-a-fast-internet-connection-when-you-need-it](http://lifehacker.com/326543/ensure-a-fast-internet-connection-when-you-need-it)

---

### Post by oldos2er on 2013-04-21
Moved to Networking & Wireless.

---

