---
title: "help with server not connecting to net"
date: 2012-01-13
forum: Networking &amp; Wireless
---

### Post by zinzara on 2012-01-13
Hi, I'm a little new to linux and networking. I have a small server that I want to use as storage for my home network. I have a wireless router acting as a bridge that is getting wireless signal from our main router in the home and turns the signal into wired for my network. I have a 8 port switch hooked to the router which all my computers are connected to. Everything works fine if I just use DHCP. But when I set my server to a static IP it won't connect to the internet. I can ping the server from other computers. I want this server to be accessible outside the network. I'm running Ubuntu Desktop 11.04. Diagram of my network:

Main_wireless_router~~~~Bridge---Switch---Server_and_Computers

Just to see if my network settings are correct:

Server IP - 192.168.1.148 (got this from when it was DHCP).
The rest I got from another computer on the network which can access the internet:
Netmask - 255.255.255.0
Gateway - 192.168.1.1

I've tried all the ifdown, ifup, and putting the settings in the interfaces file. Won't let me get on the net. Switch it back to dhcp and it works just fine. Please help.

---

### Post by jsra on 2012-01-14
Hi,
problem can be in DNS settings, DHCP server assigns you DNS automatically. Check your /etc/resolv.conf. You can determine if this was the problem by ping to some known IP, eg 8.8.8.8 and some url.

---

