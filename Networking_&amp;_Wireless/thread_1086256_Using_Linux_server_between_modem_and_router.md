---
title: "Using Linux server between modem and router"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by Hellsheep on 2009-03-03
Hello, i am trying to achieve something rather unknown to me, at home we have a lot of troubles with internet bandwidth mysteriously going missing etc, so i am trying to employ a method of tracking that using certain tools, but to do this i am aware that i would need to set up the network to have the internet routed through my linux machine.

Basically, the trouble i am having is this: I want to connect my phone line to the modem (IConnect Access 621) and then connect the modem via ethernet into the Ubuntu server machine, which then via another ethernet adapter it sends the internet to my switch/router which routes the internet out to the individual computers.

My problems are everything really, i have no clue how to do it, what to do and whether i can use 1 PCI ethernet card and 1 onboard ethernet card, or do i need to use 2 PCI ethernet cards, or a dual PCI ethernet card?

Can someone please shed some light on an easy way to achieve:

Phone Line>Modem>Server>Switch>Computers

Thanks.

---

### Post by crokett on 2009-03-03
Whether you use 2 PCI adapters, a dual port adapter or one PCI and one onboard adapter doesn't matter. You just need two ethernet ports.  Lets call them Port 1 and Port 2 and pretend that the modem is connected to port 1 and the router is on port 2.   You need to configure the Ubuntu server to share the internet connection on port 1. connection. To make things easier I would make the IP address for port 2 a Static address.  

You would configure the router WAN port to have a default gateway of the IP address that is assigned to port 2 and the name server, etc are  the same as whatever the name server is that gets assigned to port 1 of the Ubuntu machine.

---

### Post by madverb on 2009-03-04
Take a look at ebox.

[www.ebox-platform.com](www.ebox-platform.com)

---

### Post by Hellsheep on 2009-03-04
> **crokett said:**
> Whether you use 2 PCI adapters, a dual port adapter or one PCI and one onboard adapter doesn't matter. You just need two ethernet ports.  Lets call them Port 1 and Port 2 and pretend that the modem is connected to port 1 and the router is on port 2.   You need to configure the Ubuntu server to share the internet connection on port 1. connection. To make things easier I would make the IP address for port 2 a Static address.  

You would configure the router WAN port to have a default gateway of the IP address that is assigned to port 2 and the name server, etc are  the same as whatever the name server is that gets assigned to port 1 of the Ubuntu machine.

Okay, i have a ethernet PCI card set up and a onboard one set up, if i plug the modem into the phone and then the ethernet to the PCI card, and plug the onboard to the router and route the connections out then, where do i go from there? How do i set up static IP address for Port 2, and how do i make port 1 share the connection etc? Sorry i am new to commands. If you could provide a detailed information on how to do it, that would be great.

---

