---
title: "Internet Connection Sharing DHCP3"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by bjpech on 2009-04-09
My question refers to the Page in the documentation site: [https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3]("https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3")

I am novice on UBUNTU. My question is: in the network figure shown on the page, can "eth0" be a wireless connection and the DCHP server a DSL wireless box provided by an ISP?

Second question can"eth1" and the bridge be a wireless network.

Here is the problem I am trying to solve. I am sharing an internet connection with a neighboor using wireless. I can only get good connection in a specific place in my cabin. I want to be able to connect from anywhere in the house. I do not want to buy two wireless router capable of relaying each other (from apple for example). Instead I want to use an old PC to serve as a router. The PC connects to my neighboor though his wireless network. I have a Netgear wireless router which I can interface to the PC through an internet cable. I cannot solve the problem with Windows NT client (server is needed), so I am thinking of using Ubantu. THANKS.

My neighboor wireless box does address translation and, I assume, multiplex a single global IP address. SO I am not sure if that does not screw up the UBUNTU DHCP3.

Thanks. Bernard

---

### Post by bjpech on 2009-04-10
The documentation makes clear that "eth1" can be a wireless network. My question is still can eth0 be a wireless network?

[https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3?action=AttachFile&amp;do=get&amp;target=ConnectionSharingDHCP3_ver3.png]("https://help.ubuntu.com/community/Internet/ConnectionSharingDHCP3?action=AttachFile&amp;do=get&amp;target=ConnectionSharingDHCP3_ver3.png") 

Thanks. BJ

---

### Post by superprash2003 on 2009-04-10
possible..but usually no.. as your inbuilt LAN card would usually take eth0. type iwconfig in your terminal.. you would come to know your wifi interfaces

---

