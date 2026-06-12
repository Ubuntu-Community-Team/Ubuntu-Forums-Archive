---
title: "How to setup a an ad-hoc wireless with one acting as router"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by rickyrockrat on 2010-03-06
While trying to get a r8168 driver working, I had to set up an ad-hoc network, with one machine acting as a router with connection to the internet.  This will work, but I'm sure it's a hack.

We have two machines. One, we'll call Router has a working wired and wireless NIC on it. The other we will call Itsbroke, and it has the non-working wired NIC, but a working wireless NIC (the Rosewill USB RNX-G1 seems to work).

First, edit the /etc/network/interfaces file in each machine. The entry should look something like this:

iface eth1 inet static
address 192.168.3.x
netmask 255.255.255.0
wireless-essid ductape
wireless-channel 3
wireless-mode ad-hoc
wireless-rate 11M
wireless-ad 1e:65:ad:28:f8:fa
down ifconfig eth1 0

On Itsbroke, x in address above should be 3, and add this line 
gateway 192.168.3.1
On router, x should be 1

On Itsbroke:
ifup eth1
on Router, the easiest thing is just to download the firewall scripts, which by the way, include a ssh blacklist feature, and lock your box down pretty tight.  I'm sure they need work, I was in a hurry to hack the wireless stuff in. The firewall-2.4 goes in /etc/init.d and should be owned by root and executable. The rc.firewall-2.4 goes in /etc

On Router:
ifup eth0
ifup eth1
/etc/init.d/firewall-2.4 restart

Make sure the two boxes can ping each other, then find out the nameserver in Router's /etc/resolv.conf, and add that entry into Itsbroke /etc/resolv.conf, and you should be good to go.

*NOTE* The attachment scripts leave the firewall at ACCEPT, instead of DENY, which may or may not be a good thing. If you are testing, it's a good thing. If you are running for real, it's a bad thing.  Edit the firewall-2.4 file and change the ACCEPT to DENY to change this.

---

