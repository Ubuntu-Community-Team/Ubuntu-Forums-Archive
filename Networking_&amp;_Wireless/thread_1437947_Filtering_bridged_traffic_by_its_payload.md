---
title: "Filtering bridged traffic by its payload"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by crazyjackdavis on 2010-03-24
I'm attempting to bridge two network interface cards - eth0 and eth1 - using a laptop computer running Ubuntu 9.1.

Now here's my question as it's a little dicey.  Realizing that bridging is a layer 2 process, I'm wondering if I can do a deep frame analysis to read the Ethernet payload without binding an IP address to the interface.  I'd then like to filter on a (layer 3) destination port, denying any of this traffic to the other side of the bridged interface.

I've attached a graphic illustration of what I'm trying to do.

Essentially I want to monitor Internet traffic and be able to connect to my laptop from anyplace in the world to review what I've captured.  I don't however want these packets re-broadcast to the "computer".

Is this possible?  Are there tools that already do it?

Jack

---

