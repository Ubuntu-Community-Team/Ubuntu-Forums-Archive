---
title: "Networking Setup"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by thetigergo on 2009-11-16
Hello everybody!
Good day to all!

Does anybody can give me an advice?
I am working in a local government firm. We are having trouble with our network setup. We would like to re-setup our network because we having trouble of our IPs. Duplicated in more than one computer.

Can anybody give me a diagram or illustration how I am going to setup a metropolitan area network? I know few things how to confgure a routers and a manageable switches but I do not know how to set it up. I mean how many routers that I am going to use and how many switches I am going to put.

My plan is we have a centralized data center. Where all our servers is located. We have 18 to 20 offices inside a compound and few of it are outside compound. We have plan that every office we make a different subnet. For example we will use an IP range of 172.16.0.0 - 255 for office1 and use 172.16.1.0 - 255 for office2 and 172.16.2.0 - 255 for office3 and soon. Now my problem is how I am going to set it up. How many router I am going to put up and how many switches or manageable switches do I put into?

I would like to thanks to a person or people who can give me a diagram of this network layout.

Thank you so much for the support and God bless.

Felix :(

---

### Post by ArcaVex on 2009-11-16
Well i take it you are going for a wired network and not wireless.

Depends on the number of network devices in each office (PC, printers, etc). You'd save money of course having 2 rooms linked to one 48port switch. or you could have 2 x 16 port or whatever. 

But for example you'd have a switch in each office, so thats 18 switches. One switch in the server room. Each office switch is linked via uplink to the switch in server room.  (Or can be connected via a patch panel for ease of use and neatness)
Server would be connected to a router/dsl modem for broadband/phone. 
If you needed wireless support for laptops you could attach a wireless access point into the network.

Do you really need a different subnet for each room? or is this just to make it more manageable for humans? :D

---

