---
title: "One computer and two networks, how should I set it up?"
date: 2009-01-11
forum: Networking &amp; Wireless
---

### Post by fissionmailed on 2009-01-11
Ok, I have one computer and I want to connect it to two networks. The computer in question has two NICs. Basically I want all my internet traffic  to go through network 1 but samba through both(network 1 and 2).  One option is to connect network 1 and 2 to the computer. The other is to connect the routers.  I have tomato firmware on network 1 and network 2's routers is a netgear one(I'm borrowing it from a friend longish term so I don't want to put different firmware on it). 

What do you guys think I should do?

---

### Post by Cocoabean on 2009-01-11
I've tried this, you'll have to manually set up routes, it will not be fun. Your best bet is to merge the two networks. Why are they split? You could easily bridge them or, if you just need more ports to plug into, turn off DHCP on one router, and connect an ethernet cable from one of the lan ports of that router to one of the lan ports of the other. If you are running the samba server on the dual-nic computer, you can tell samba to bind to the IP of the nic of the second network. But really, I don't see a reason why you need two separate networks??

---

### Post by fissionmailed on 2009-01-16
> **Cocoabean said:**
> I've tried this, you'll have to manually set up routes, it will not be fun. Your best bet is to merge the two networks. Why are they split? You could easily bridge them or, if you just need more ports to plug into, turn off DHCP on one router, and connect an ethernet cable from one of the lan ports of that router to one of the lan ports of the other. If you are running the samba server on the dual-nic computer, you can tell samba to bind to the IP of the nic of the second network. But really, I don't see a reason why you need two separate networks??

Two internet connections. That's why. 

Now I know what I'm looking for I'll google for setting up some routes. Before I didn't even know what to google for. *facepalm*

---

### Post by fissionmailed on 2009-01-17
Update: I've decided that messing with the routes in my computer is going to take a lot longer than trying to configure the router to do it.  

My router with tomato automatically connect to the other router(I pinged it and it seems to work).  I just need to find a way to made it so that all traffic from the other router (at that router's assigned IP for my router) get's forwarded to my computer. I'm not sure if just forwarding all the ports would word or not. I'm have to give it a try and see if it works.

---

