---
title: "SSH config"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by bkulaga on 2009-06-03
Hello, I am somewhat new to linux, I have used slackware but about 4 years ago so I forgot a bunch of things. 
With the sshd_config.... I want to know how to set it up where I can connect to it outside of my home network... I have a router and two computers connected to it. This is what I put in my actuall sshd_config file: 
# What ports, IPs and protocols we listen for
Port 2222
# Use these options to restrict which interfaces/protocols sshd will bind to
ListenAddress 127.0.0.1
ListenAddress 192.168.2.1<---- my router adress 
ListenAddress 1**.1**.*4*.211<----this is my actuall IP adress 
ListenAddress 192.168.2.101<-----my computer address where I am going to run SSH

Is this correct? What should I add? What should I take out??? 
Please help out 
Thank you.

---

### Post by Iowan on 2009-06-03
Router address will probably be unnecessary. (But I thought multiple ListenAddress lines would override previous lines - **man** page suggests otherwise...)
The actual IP address - that's the router's external address?

---

### Post by DGortze380 on 2009-06-03
You'll need to set up port forwarding on your router to send port 2222 to the internal IP of the machine we want to connect to.

You can then access it via your routers public IP or a service like dyndns.org.

I suggest using pubic/private keys instead of username/password.

---

### Post by Brandon Williams on 2009-06-04
The ListenAddress should be the primary IP address of the machine that is running sshd. It is not used to specify the allowed client IP address(es). If you want to allow connections on both localhost and all of the sshd machine's IP address, then there is no need to specify a ListenAddress ... it will listen on all if you don't limit it by specifying a subset.

If you want to limit who is allowed to connect to ssh based on client IP addresses, you can use iptables rules.

---

