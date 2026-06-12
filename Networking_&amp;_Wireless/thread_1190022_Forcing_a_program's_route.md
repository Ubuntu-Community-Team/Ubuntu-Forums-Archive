---
title: "Forcing a program's route"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by sq377 on 2009-06-17
If it's not supported in the application directly, how do I tell a program to go through a specific interface? My default route is to eth0, but I want one program to communicate through wlan0.

Thanks

---

### Post by puppywhacker on 2009-06-17
I don't think you can, unless you run it in a jail or virtual machine with different routing tables. I think so because the ip-stack is supposed to be decoupled from the applications by design.

If you can do it it's probably something funky in netfilter. which you can configure with ipfilter or tc

---

### Post by jonobr on 2009-06-17
Hello

Puppywhacker is correct.

The OSI 7 layer model is on the wike [here]("http://en.wikipedia.org/wiki/OSI_model") 

The way that its designed is to allow application to talk to applications using this layering model.

Each layer provides support to the next layer.

The IP functionality occurs at layer 3, the networking layer.
The transport layer, layer 4 decides how it should get there or be transported.

As a packet travels down the layers to get onto the network, each layer adds to the packet so that its peer layer at the remote end can receive it.

The only resolution to your problem is put a route in for your data to go through a certain interface.

---

### Post by sq377 on 2009-06-17
I'd love to do this in a jail, but aren't the routes are held in the kernel?  Also the system I'm using is lacking any kind of real VM support.  

I'm trying to run a torrent client this way, can anyone recommend one that allows this?  I've looked around with no real luck.

Thanks a lot everyone

---

### Post by DGortze380 on 2009-06-17
You'd have to route the TRAFFIC, not the application, using iptables.

Random example, if your program uses TCP over port 15000 you'll want a rule that says allow all TCP traffic from any to any on port 15000 through interface wlan0.

---

