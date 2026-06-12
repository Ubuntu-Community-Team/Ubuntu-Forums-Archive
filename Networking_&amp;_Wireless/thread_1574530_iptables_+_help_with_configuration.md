---
title: "iptables + help with configuration"
date: 2010-09-14
forum: Networking &amp; Wireless
---

### Post by piotbr4 on 2010-09-14
Hi, 

i am relativly new Ubuntu user and I have following network problem;in my host computer I have two interfaces, eth0 (192.168.56.102) to connect with ouutter web and localhost.Additionally I am using specialistic app, which unfortunatly can only listen for incoming messages on localhost.My aim i to make following packet forwarding:

INCOMING PACKET: destination address(192.168.56.102:5060)---> 127.0.0.1:506
OUTGOING PACKETS: source address(127.0.0.1:5060)---->192.168.56.102:5060,

so that I can both receive and send packets using my faulty app.

As I mentioned I am really amateur, ut I read a lot and I thinkit would be possible with IPTABLES,am I right? I would like to aks for help, I tried configuring ip tables on my own, unfortunately without any effects.

Thansk in advance,

Piotr

---

