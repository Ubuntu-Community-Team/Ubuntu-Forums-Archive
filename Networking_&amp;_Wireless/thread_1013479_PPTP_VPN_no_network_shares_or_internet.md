---
title: "PPTP VPN no network shares or internet"
date: 2008-12-16
forum: Networking &amp; Wireless
---

### Post by afeinstein on 2008-12-16
I need to be able to connect multiple people and be like I am in the office, so I can access shared folders, print and the like.  Ideally all traffic would be routed through the office network for added encryption in wireless situations. Do I need a bridged connection? Any help would be much appreciated.

I am on intrepid 8.10, but have been using the command line for most installs.  I setup a PPTP VPN using ([http://poptop.sourceforge.net/dox/debian-howto.phtml](http://poptop.sourceforge.net/dox/debian-howto.phtml)).  If there is an easier way please advise.

I can successfully VPN into my network from an XP machine and Mac OSX.5, but I cannot access any of the shared folders on the network, or access the internet.  When I untick "use default gateway on remote network" i can access the internet, but it is not tunneled.

---

### Post by LoneWolfJack on 2008-12-17
This is probably not exactly helpful as you are using 8.10, but in 7.10, there was a setting called "refuse CHAP" that I had to enable to connect to a windows VPN.

By now, I'm using Ibex as well and just today I need to install a VPN server again... and there we go, the config interface has changed and there's no refuse CHAP thingy and I'm (once again) not able to get the VPN client connect to the server. In fact, now that they got rid of the error messages as well, I'm probably in for a few hours surfing the web trying to find a solution. Not that I would have work to do...

---

### Post by afeinstein on 2008-12-17
Thanks for your response. Maybe I was a little unclear.

I am trying to configure Ibex as the server.  I successfully connect, but I cannot see any shared folders.

Let me know if you experts out there need IPs or gateways or any other mumbo jumbo. Thanks!

---

