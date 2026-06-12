---
title: "Setup server"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by JFASI on 2009-05-23
I want to set up an old computer of mine as a file dump, ssh, and svn server, and I want access to it from everywhere I go. I have two issues that I would need resolved: 

1. I don't want to go through all the trouble of actually getting an actual domain name, so I would want to address this thing via its IP address. I believe, however, that my ISP will most likely shuffle my IP address. Is it worth calling and asking them if they could stabilize it? 

2. This computer is behind a router, and has an IP address like 192.168.x.x. How can I give it a real address? 

Thanks for reading.

---

### Post by ALIENDUDE5300 on 2009-05-23
> **JFASI said:**
> I want to set up an old computer of mine as a file dump, ssh, and svn server, and I want access to it from everywhere I go. I have two issues that I would need resolved: 

1. I don't want to go through all the trouble of actually getting an actual domain name, so I would want to address this thing via its IP address. I believe, however, that my ISP will most likely shuffle my IP address. Is it worth calling and asking them if they could stabilize it? 

2. This computer is behind a router, and has an IP address like 192.168.x.x. How can I give it a real address? 

Thanks for reading.

As for not getting an actual domain-name, you can use a service such as DynDNS.com

---

### Post by Wiebelhaus on 2009-05-23
Yea there's services out there that will supply you with a static IP , your service provider probably won't.

---

### Post by JFASI on 2009-05-23
> **ALIENDUDE5300 said:**
> As for not getting an actual domain-name, you can use a service such as DynDNS.com

Awesome, I went and got a basic account there, but now I just need to make my IP address be constant. What services can I use to get that? 

Also, IP address aside, I have a new concern. I am having a hard time ssh'ing into the machine through the new DNS name. In fact, I can't ssh into it at all through either the address or the hostname. 

EDIT: It turns out that what I have entered into the dyndns.com form was my ISP's server, where I would naturally be refused access. How can I get my own address? Will it involve some wrangling with the ISP?

---

### Post by Iowan on 2009-05-24
Your ISP will *probably* be willing to $ell (more accurately, rent) you a static IP address, but that's what DynDNS *should* do - make your dynamic address look like a static one (or at least make it accessible by name).  You may still need to set up port forwarding on your router. It's possible that the router is refusing the connection.

---

### Post by shel-hall on 2009-05-24
> **JFASI said:**
> I want to set up an old computer of mine as a file dump, ssh, and svn server, and I want access to it from everywhere I go. I have two issues that I would need resolved: 

1. I don't want to go through all the trouble of actually getting an actual domain name, so I would want to address this thing via its IP address. I believe, however, that my ISP will most likely shuffle my IP address. Is it worth calling and asking them if they could stabilize it? 

2. This computer is behind a router, and has an IP address like 192.168.x.x. How can I give it a real address? 

Thanks for reading.
Ask your ISP if they will give you a static IP address; mine does it for an exra $5.00 per month on my bill.

Set up your router's "port forwarding" capabilities to forward external connections on port X (see further down) to your new server.  This will provide an incoming path from your ISP-issued static external IP address through your router's NAT system to your server's internal 192.168.x.x address.

Set up the SSH server daemon ("sshd") on your server.

For testing purposes, use the default SSH port (22) both for the port forwarding and for the SSH daemon. You'd forward port 22 on your external address to port 22 on your internal address, and have "sshd" use its default port.

Once you get it all working and understand what's happening, you might want to change it all to some other port, as a way of avoiding at least some of the attacks aimed at weak SSN implementations and installations.  As an additiona defense, consider firewalling any part of the world from which you don't expect authorized access.

-Shel

---

