---
title: "Port Forwarding: What should I know and how can I make it safer?"
date: 2011-07-18
forum: Networking &amp; Wireless
---

### Post by sirspazzolot on 2011-07-18
My understanding is that port forwarding is how you get traffic sent to a router:port to be transferred to the computer:port inside the network. Is this right, or is it oversimplified? I know that there are risks but I don't really know the extent of them. What are the risks and how can I minimize them? Assume that Linux will be running when doing anything with forwarded/opened ports. Does port forwarding pose a risk to the network, or mostly just the computer? Thanks in advance. :D

---

### Post by foxmulder881 on 2011-07-18
> **sirspazzolot said:**
> My understanding is that port forwarding is how you get traffic sent to a router:port to be transferred to the computer:port inside the network. Is this right, or is it oversimplified?

That's basically all there is to it mate.

As a basic rule of thumb, just keep all ports closed and only forward the ones you really require. Eg. torrent port.

---

### Post by sirspazzolot on 2011-07-18
Well, I plan to screw around with server things so I think I'd need a few. I don't intend to leave anything running. I'd probably re-close all of my ports after a few days, tops. I just have to convince my mother to let me, since it's a family network with all of our computers. Also lol at my accidental emoticons. Thanks for the answer!

---

### Post by foxmulder881 on 2011-07-18
Remember to open the ports in any software firewall also. Otherwise the port forwarding will be useless.

---

### Post by sirspazzolot on 2011-07-18
Oh, I'll be running Ubuntu, no software firewall over here.

---

### Post by foxmulder881 on 2011-07-19
You're not using ufw? Although not enabled in Ubuntu out-of-the-box, it's still included by default.

---

### Post by sirspazzolot on 2011-07-19
Didn't know there was one. I'd enable it but I don't plan to leave anything running for more than a few days, so I think configuring a firewall is more hassle than it's worth. Thanks for all your responses, foxmulder. It's greatly appreciated. I guess I'll repeat an earlier question now because it's been bugging me overnight. Would forwarding a port for a webserver or whatever jeopardize my whole network, or mostly just the computer running the server?

---

### Post by foxmulder881 on 2011-07-19
> **sirspazzolot said:**
> Would forwarding a port for a webserver or whatever jeopardize my whole network, or mostly just the computer running the server?

Should only affect the system which is running the webserver. Unless of course you're running some weird internet connection sharing configuration of your network.

---

