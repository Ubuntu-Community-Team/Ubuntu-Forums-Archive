---
title: "Ad hoc Network OpenVPN"
date: 2013-02-25
forum: Networking &amp; Wireless
---

### Post by mculprit on 2013-02-25
I am setting up a wireless ad hoc  network between a few linux machines with Ubuntu 12.04. My company's  security wants me to use VPN for securing the network. I'm following the  tutorial at [https://help.ubuntu.com/12.04/serverguide/openvpn.html](https://help.ubuntu.com/12.04/serverguide/openvpn.html).  So reading this, it seems to me that I could just put a certificate  server on a master node and then just give every other computer client keys. To let all the computers talk to each other, I'll have to change the configuration file on the server to allow "client-to-client" communication.

However, I'm curious if it's possible to set up the ad hoc network so it's completely decentralized. Having a master node limits the possible physical spread of the network. Any ideas on how I can set up such a network?

---

### Post by SeijiSensei on 2013-02-25
> **mculprit said:**
> Having a master node limits the possible physical spread of the network. Any ideas on how I can set up such a network?

Why?  Passing packets around is a pretty insignificant task for most modern CPUs.  You could easily support hundreds of machines from a single server.  

In fact, as long as the server and client can see each other, they can set up an OpenVPN connection.  If you have the routing configured properly, the clients can be scattered across the world and still be peered with one another over the common IP subnet that the VPN creates.

I think the model you propose is sound.  Why don't you give it a trial run?

---

### Post by mculprit on 2013-02-25
Our network is isolated. The idea is that the nodes could be spread out over a physical region and still use wireless to keep up a network. So a master node that is required makes a weaker networking capability since all the other nodes would have to be within range of the master node.

I want the network to be able to work no matter what node goes down, if for some reason it does. I have a legitimate reason to believe that a master node may be shut down or disconnected. And if this happens, I need the other nodes to still continue to talk to each other.

---

### Post by SeijiSensei on 2013-02-27
I see those concerns more as an wifi engineering issue than something that OpenVPN might fix.  I'm sure there must be people who specialize in desigining wide-area wireless networks.  Perhaps "[mesh networking](http://en.wikipedia.org/wiki/Mesh_networking)" is what you're looking for.  Here's [one Linux-based implementation]("http://www.linuxplanet.com/linuxplanet/tutorials/6758/1") I found.

---

### Post by mculprit on 2013-02-27
Ahh, mesh networking seems to be the terminology that I'm looking for. Thanks, it's helping out in refining our search. The link you showed isn't quite what we need, but it's a good start. Thanks for the help.

---

