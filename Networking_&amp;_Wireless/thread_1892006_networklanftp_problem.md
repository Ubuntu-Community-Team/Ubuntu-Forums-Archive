---
title: "network/lan/ftp problem"
date: 2011-12-07
forum: Networking &amp; Wireless
---

### Post by tb2012 on 2011-12-07
Hi,

I have "small" or "not so small" network problem/missing understanding on Ubuntu 10.10 as follows:

I have two LANs (192.168.1.x and 192.168.0.x). My box connects to LAN 192.168.0.x, my ftp server is on LAN 192.168.1.x  ---- now as soon as I am connected to a VPN I cannot access the ftp any longer.

How do I solve this? Routing problem?

Thanks :) for enlightenment


PS: When my box is connected onto same LAN (192.168.1.x) my ftp access is fine whether or not I am using a VPN

---

### Post by dmizer on 2011-12-08
> **tb2012 said:**
> Hi,

I have "small" or "not so small" network problem/missing understanding on Ubuntu 10.10 as follows:

I have two LANs (192.168.1.x and 192.168.0.x). My box connects to LAN 192.168.0.x, my ftp server is on LAN 192.168.1.x  ---- now as soon as I am connected to a VPN I cannot access the ftp any longer.

How do I solve this? Routing problem?

Thanks :) for enlightenment


PS: When my box is connected onto same LAN (192.168.1.x) my ftp access is fine whether or not I am using a VPN

What is the VPN subnet?
Do you have your VPN configured via network-manager?

---

### Post by tb2012 on 2011-12-08
What is the VPN subnet?
>>> VPN connects through 192.168.0.x, which connects to 192.168.1.x .... both standard subnet 255.255.255.0 ..... VPN subnet when active is of course set by provider and different. B U T  that doesn't seem to be the problem (?!), because ftp works if it is in the same LAN as my connect to VPN. 

As I said as soon as VPN is not active I can connect to ftp whereever it is (here:192.168.0.x, or 192.168.1.x .). What is blocking it, I can't grasp to understand 

Do you have your VPN configured via network-manager?
>>> No, I use gopenVPN

---

### Post by jonobr on 2011-12-08
Hello


I would recommend comparing your routing table before and after you connect your VPN.
(guessing dmizer may have been implying a routing issue because the subnet at the other end of the VPN may have been on the same subnet causing a routing issue.)

Anyway, It does sounds as if all your traffic maybe routing over the VPN when its up which i dont think is the default action for openvpn.

Easiest way to find out is to trace on your eth0 for ftp

```
sudo tcpdump -i eth0 port 21
```
ftp and then i reckon no packets will be seen

Doing a traceroute to the ftp server , may even show the traceoute goining over your VPN connection but thats a guess.

Again, I figure comparing the routing tables using the 

```
netstat -rn
``` before and after connection may help.

---

### Post by dmizer on 2011-12-09
> **jonobr said:**
> (guessing dmizer may have been implying a routing issue because the subnet at the other end of the VPN may have been on the same subnet causing a routing issue.)
Yes, if your VPN is on the same subnet, your local routing will not work properly. You have 3 (in your case 4) network routes to consider. The local LAN network, the VPN network, and the LAN at the VPN server side. If the IP range on any one of these networks matches, you'll have routing problems like what you're experiencing.

---

