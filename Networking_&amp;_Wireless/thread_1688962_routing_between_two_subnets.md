---
title: "routing between two subnets"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by amr.labib on 2011-02-16
Hi,

I have a network routing problem that I need to fix using a PC with ubuntu installed. Here are the details of my problem:

- I have two networks.
- The first network is an ADSL router with subnet 192.168.1.x. I do not have access to the router nor change any of its configuration.
- The second network has a subnet 172.26.x.x and connect via a wireless access point. Some of the devices connected to the network require to have static IPs.
- I have a PC with ubuntu installed and two ethernet cards: one connected to the first network and the other connected to the access point. 
- I need to share the internet connection between the two networks using ubuntu. I already tried before on windows and the sharing worked when both networks were configured to use the same subnet. Once I changed the subnet of the second network, internet sharing stopped working.

Can you help me out in this?

Thank you very much.

---

### Post by mips on 2011-02-16
[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)
[https://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/](https://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/)

You cannot have both interfaces in the same subnet, it won't work as you have found out.

---

