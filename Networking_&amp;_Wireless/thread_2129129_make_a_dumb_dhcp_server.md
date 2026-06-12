---
title: "make a dumb dhcp server"
date: 2013-03-25
forum: Networking &amp; Wireless
---

### Post by ulao on 2013-03-25
I use iptables NAT for my systems I have behind my ubuntu server. I set up a v-nic at 192.168.0.19 that I use as a gate way of sorts. I then set a 192.168.0/24 if to all my systems I use. The problem I have is when people come over with there smart phones and want to get on my network. I then have to give them an ip to use and they need to put in a dns/gateway. What I want is a way for then to pull an ip automatically. I'm thinking I dont need to set up a full blown DHSP and I'm not sure if that will cause issues with iptables. 

I guess at most I need to give out an ip, gateway, and dns. Any suggestions, I tried installing a dhcp but there were major dependency issues. Looking for a minimal simple solution here.

---

### Post by jonobr on 2013-03-27
Hello


What are the major dependencies?

There are two options if you don't want to install a DHCP server.

Install a device to hand out IP address on your network, like a cheap router.
Or get people to configure static information on their devices.

---

### Post by ulao on 2013-04-02
Yeah I tried the dhcp option on my router but it wants to be the gate way. I can not get it to just hand out ip's without it handing out a gateway. 

I guess Ill try to install a DHCP again and list the errors I get. I was hopping for an easy DHCP server out there, I think I just did a apt-get install dhcp.

---

### Post by Doug S on 2013-04-02
You would want to do this:```
apt-get install isc-dhcp-server
```You should not have troubles with your iptables rule set, but you will need to allow UDP INPUT from the internal interface from port 68 destined for port 67. The [ubuntu server guide ]("https://help.ubuntu.com/12.10/serverguide/dhcp.html")is a good reference.

---

