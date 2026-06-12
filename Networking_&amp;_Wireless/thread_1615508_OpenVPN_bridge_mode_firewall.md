---
title: "OpenVPN bridge mode firewall"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by linuxmunky on 2010-11-07
Hello there,

I have OpenVPN running on my Ubuntu Server just fine.  I can connect over the Internet and access all my resources on the LAN via bridged mode perfectly.  My server only has one LAN card and sits behind my router, which means it has a private IP address of 10.1.1.2.

...Which brings me to my question.  I want to open up access to my friends via OpenVPN, but I don't want them to be able to access other machines on my LAN (e.g. 10.1.1.20).  However, I do want them to be able to talk to each other and pass broadcasts (old LAN games), as well as my laptop (let's say 10.1.1.7).

I've tried using iptables to block traffic to the LAN (such as .20), to no avail.  I've been reading up and it seems as though iptables won't even filter the traffic, as it's passed at a lower layer.  Is this true?  If so, what do you recommend I do in order to prevent my buddies from accessing the rest of my LAN while siumultaneously allowing broadcasts pass for some very old Windows LAN games (we're talking Windows 98).

Thanks all, I appreciate your reading and hopefully your response!

---

### Post by linuxmunky on 2010-11-08
Well, developments for anyone who's having a similar issue.  I approached the issue in another direction and I THINK I'm getting closer.

My server has two NICs.  Therefore, I set it up as so:

eth0: 10.1.2.2 255.255.255.240
eth1: 10.1.1.2 255.255.255.0
br0 uses eth1 and tap3
br1 uses eth0 and tap5

I set the OpenVPN server to use br1 instead of br0 with the server-bridge option, but kept the port forwarding rule on my router to point to the 10.1.1.2 computer.  Success!  I can VPN in and it gives the PC a 10.1.2.3 address.  It can talk to the server just fine, yet it can't see my 10.1.1.0 network (which is what I want for security reasons).

I just need this last little bit of help.  How can I allow my laptop on my LAN (10.1.1.100) talk to a VPN client (10.1.2.3)?  That's all I need to do.

I'm sure this is a bit confusing and wouldn't mind explaining it further if you could provide assistance.  Thanks!

---

### Post by linuxmunky on 2010-11-08
Thought I would include a diagram, as I'm a visual learner.  Basically, I want the laptop (10.1.1.100) to communicate with the eth0 interface on the server so I can talk to the VPN clients.  However, I do not want the PC to talk to or even be able to see the VPN traffic (and vice versa).

Am I looking at creating static routes on the clients?  Do I have to do anything on the router?  These seem like basic networking questions, so I appreciate the help.

Thank you!

---

