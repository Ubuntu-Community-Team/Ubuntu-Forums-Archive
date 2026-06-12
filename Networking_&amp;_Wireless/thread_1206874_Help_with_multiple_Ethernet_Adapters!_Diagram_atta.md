---
title: "Help with multiple Ethernet Adapters! Diagram attached"
date: 2009-07-07
forum: Networking &amp; Wireless
---

### Post by spelunker on 2009-07-07
A server of ours crashed that someone else configured (who sadly is no longer with us) and I have to get our server backup. I reinstalled Ubuntu 9.04 desktop and am having trouble getting the networking back up.

Here is the situation. We have 3 ethernet adapters in our machine. 1 (eth0) which connects us to the outside world/internet, 1 that hooks to our own private subnet with 10 computers, and 1 that clicks us into someone else's subnet so we can talk to a machine on their network.

How do I get the networking set up properly so that the computers that are on my 172.16.2.* subnet can talk to the outside world? I set entered all the proper information (I think...) and the only one who can access the outside world is the server. Here is the adapter info I have entered:

**eth0** Ip: 10.0.23.51, subnet: 255.255.255.0, default gateway: 10.0.23.24
**eth1** Ip: 172.16.2.1, subnet: 255.255.255.0, default gateway: 10.0.23.24
**eth2** Ip: 172.16.1.129, subnet: 255.255.255.0, default gateway: 0.0.0.0

Also, I want to run a DNS and DHCP server on my server so that everyone in the 172.16.2 subnet can ssh around without typing ip's and guests can click into our network and go. I installed dhcp3-server, configured it to bind to eth1 and the computers on the 172.16.2 subnet now get ip's properly and point to my dns server. I'm not sure sure I have the dns set up properly though. It works locally, but I'm not sure I'm passing them to the isp's dns servers properly. Perhaps I'll go with something easier to configure like dnsmasq since I'm getting a little tripped up on the DNS configuration.

So, do I use bridging or NAT or soemthing that I don't quite understand to get the subnet pc's to the interent? Anyway, clearly I'm confused!

---

### Post by Iowan on 2009-07-07
For DNS/DHCP, check into DNSMasq.  
Do you have a fixed IP address for your internet access, or does your ISP use DHCP? 
Do you connect via router, modem, or otherwise?

---

### Post by spelunker on 2009-07-07
> **Iowan said:**
> For DNS/DHCP, check into DNSMasq.  
Do you have a fixed IP address for your internet access, or does your ISP use DHCP? 
Do you connect via router, modem, or otherwise?

Yeah, I think I'll try DNSMasq. Bind9 was getting a little heavy for my current level of knowledge.

I do have a fixed IP for my external adapter. It is given to us by the parent organization that my network is in. I then connect through 10.0.23.24 which is their router that connects us to the outside world.

Still though, how do I get my internal computers to talk to the outside world?

---

### Post by superprash2003 on 2009-07-08
i think you basically need to configure intenret connection sharing.. where one interface is the source of internet and the other is the interface which is connected to the local network.. check out this guide [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

