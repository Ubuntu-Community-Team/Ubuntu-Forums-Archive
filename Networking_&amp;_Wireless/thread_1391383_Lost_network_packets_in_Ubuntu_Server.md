---
title: "Lost network packets in Ubuntu Server"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by jherazob on 2010-01-26
Ok, question. Here's the setup, in an ugly quick-and-dirty Dia diagram:

[http://i.imgur.com/rQuRw.png](http://i.imgur.com/rQuRw.png)

Proxy is Ubuntu Server 8.10, the vpn device is all handled by the ISP, and has it's own netconnection, it's 100% out of our hands.

Everything in the main office uses the linux proxy as default gateway. 

Problem: Random client on the branch office tries to use the services of the domain controller, it fails. Can't do dns with it, can't join the domain, nothing like that, yet ping works just fine. 

Wireshark on both sides: on the client it shows the requests being sent and resent and reresent, never answered. On the win2k, it shows all request being received and answered.

Lots of experimenting and sniffing reveal that the response packages somehow die on the linux proxy: setting the default gw of the win2k server to the main internet appliance (which has a static route to the vpn device) makes it work just fine, setting the vpn device itself as gw makes it work just fine too. Setting a static route on the win2k to send all the traffic to the 5.0 lan through the vpn device makes it work just fine. Yet even with the static route added on the linux server, the problem persists.

The real problem here is that the domain server is just one symptom. There's other servers too, and when i created a shared folder on some client on the main office and tried to access it from the client on the branch it also failed, with the same symptoms, which means that duct-taping it with static routes will be problematic. Can be done, but the problem will still be there on the ubuntu server somewhere, ready to pop up at some other time.

Any ideas on what to look for? There's a static route on the linux server as i said (all traffic to the 5.0 network pass it through the vpn gateway), iptables is set to allow all in all chains, and there's no servers on the 137-139 and 445 ports on the linux server. what else could be wrong here? i'm kinda stumped now.

---

