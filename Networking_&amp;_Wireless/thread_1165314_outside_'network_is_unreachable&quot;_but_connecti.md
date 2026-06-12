---
title: "outside 'network is unreachable&quot; but connection is working"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by LuckyStrike2501 on 2009-05-20
Hi. I'm test running a Ubuntu 9.04 Jaunty 'LAMP' Server for my class. Its running on a PC connected wireless to my DSL Gateway. I know I have a connection in my network because I can PuTTY into the server from my other PC. Both PCs can ping each other and the gateway. 

The problem is that the Ubuntu Server can't ping [www.google.com](www.google.com) nor 64.223.161.99. And I can't sudo apt-get anything. When I sudo apt-get update (101 network is unreachable) every time. 

Here is my interface:
```
$ sudo nano /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# Main wireless network interface
auto wlan0
iface wlan0 inet static
address 192.168.0.210
netmask 192.168.0.255
network 192.168.0.0
gateway 192.168.0.1
broadcast 192.168.0.255
wpa_driver madwifi
wpa_conf /etc/wpa_supplicant.conf

```

This is the resolv.conf file:
```
$ sudo nano /etc/resolv.conf

domain domain.actdsltmp
search domain.actdsltmp
nameserver 192.168.0.1
nameserver 205.171.3.25

```

The DNS is the same used in my other PC, which can ping google. 
Any ideas where the problem is?

---

### Post by puppywhacker on 2009-05-20
I think the netmask, network and broadcast in your interfaces-file are dodgy. The netmask is supposed to be indicate which part of the ip-address is network and which part is host. The other values are deducted from the ip-address and the netmask and should be there.

netmask 255.255.255.0

As for the unreachable, it is an ip routing problem, post your ifconfig and the route table

make sure you have no funny firewall rules and don't count on ping as the ultimate connection tester, it uses ICMP which can be filter leaving ping useless. these last remarks are common pitfalls most likely not applicable to your problem.

---

### Post by Iowan on 2009-05-20
Dunno about the network and broadcast addresses, but the netmask looks like a problem.  Fix that to **puppywhacker**'s recommended 255.255.255.0 and retry.

---

### Post by LuckyStrike2501 on 2009-05-21
Wow that was it. I knew that my netmask should have been 255.255.255.0 but I just overlooked it. It's good to have a second and third pair of eyes. I'm actually surprised that it even worked in the first place!

I can ping google.com and apt-get got updated.

Thank you for your help!

---

