---
title: "IP's on the network?"
date: 2010-06-25
forum: Networking &amp; Wireless
---

### Post by McRat on 2010-06-25
Anyone know a quick way to find out what IP addy's are on a LAN network with Ubuntu?

---

### Post by barney385 on 2010-06-25
> **McRat said:**
> Anyone know a quick way to find out what IP addy's are on a LAN network with Ubuntu?

Here's something I like to reference.

ETA: Oops, my attachment is missing. Give me a sec.

---

### Post by McRat on 2010-06-25
Currently I just go to the firewall and look, but I have hunch that I could do that locally.  I have a "phantom user" that shows up on a Win machine, but not on the firewall.

---

### Post by barney385 on 2010-06-25
> **McRat said:**
> Anyone know a quick way to find out what IP addy's are on a LAN network with Ubuntu?

OK, my file was too big.

Here's some links:

[http://www.ubuntugeek.com/bandwidth*monitoring*tools*for*ubuntu*users.html](http://www.ubuntugeek.com/bandwidth*monitoring*tools*for*ubuntu*users.html)
[http://onlyubuntu.blogspot.com/2007/03/bandwidth*monitoring*tools*for*linux.html](http://onlyubuntu.blogspot.com/2007/03/bandwidth*monitoring*tools*for*linux.html)
[https://answers.launchpad.net/ubuntu/+question/28506](https://answers.launchpad.net/ubuntu/+question/28506)

---

### Post by barney385 on 2010-06-25
> **McRat said:**
> Currently I just go to the firewall and look, but I have hunch that I could do that locally.  I have a "phantom user" that shows up on a Win machine, but not on the firewall.

Yeah. Have you tried netstat?

---

### Post by McRat on 2010-06-25
Netstat showed a lot of stuff (as did ifconfig), but no IP addresses.  I'm trying to figure out who 192.168.0.105 is, but the firewall just reports a MAC addy, no other info.

---

### Post by Xbehave on 2010-06-25
DO you have access to the routers config, if so you can look at the arp cache or dhcp table to see whos connected (or has been since the last router reboot or within the dhcp timeout length)

nmap can do what you want too

alternatively this little script will try every ip (takes a few minutes (4m15s ish to run))```
for x in {1..254}; do ping -W 1 -c 1 192.168.1.$x | grep icmp_seq ; done
```

p.s replace 192.168.1 with the correct range for your LAN
```
 ifconfig | grep inet | grep -v 127.0.0.1
```
im boord so here is an all in one command```
range=$(ifconfig | grep inet | grep -v 127.0.0.1 | cut -d\: -f2 | cut -d' ' -f1 | cut -d. -f1-3) ; for x in {1..254}; do ping -W 1 -c 1 $range.$x | grep icmp_seq ; done
```
with nmap that would be
```
sudo nmap -T5 -sP $(ifconfig | grep inet | grep -v 127.0.0.1 | cut -d\: -f2 | cut -d' ' -f1 | cut -d. -f1-3).*
```
(this runs in 4 seconds, so even if you have to apt-get it nmap is going to be much faster)

---

### Post by juancarlospaco on 2010-06-25
**Why you dont ping the Broadcast ???**

*everybody are there on 255, see man ping, -b parameter*

---

### Post by xpod on 2010-06-25
> **Xbehave said:**
> DO you have access to the routers config, if so you can look at the arp cache or dhcp table to see whos connected (or has been since the last router reboot or within the dhcp timeout length)

nmap can do what you want too

alternatively this little script will try every ip (takes a few minutes (4m15s ish to run))```
for x in {1..254}; do ping -W 1 -c 1 192.168.1.$x | grep icmp_seq ; done
```

p.s replace 192.168.1 with the correct range for your LAN
**```
 ifconfig | g_P_ep inet | grep -v 127.0.0.1
```**
im boord so here is an all in one command```
range=$(ifconfig | grep inet | grep -v 127.0.0.1 | cut -d\: -f2 | cut -d' ' -f1 | cut -d. -f1-3) ; for x in {1..254}; do ping -W 1 -c 1 $range.$x | grep icmp_seq ; done
```
with nmap that would be
```
sudo nmap -T5 -sP $(ifconfig | grep inet | grep -v 127.0.0.1 | cut -d\: -f2 | cut -d' ' -f1 | cut -d. -f1-3).*
```
(this runs in 4 seconds, so even if you have to apt-get it nmap is going to be much faster)

Little typo in there for you.
Just in case anyone is trying it out. :p

---

### Post by cariboo on 2010-06-25
This question belongs in the support forums, not in the cafe.

The way I check all the ip addresses on my network is to open a terminal and type:

```
sudo nmap -sP 192.168.1.0/24
```

Moved

---

### Post by Xbehave on 2010-06-26
> **juancarlospaco said:**
> **Why you dont ping the Broadcast ???**

*everybody are there on 255, see man ping, -b parameter*
Nobody answers to broadcast pings (not even most routers) I guess its some kind of security risk```
cat /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts
``` will tell you if you'd respond to a -b

ofc if you want to be well hidden (on the ip level atleast, you can always sniff traffic/wifi connections anyway), you can play with
/proc/sys/net/ipv4/icmp_echo_ignore_all
/proc/sys/net/ipv4/conf/all/arp_ignore

p.s thanks xpod

---

