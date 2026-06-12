---
title: "Trouble with static IP"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by Mxoen on 2009-08-13
So, I've been looking around for resources to try to troubleshoot this myself, but I'm coming up emptyhanded. Here's the situation:

I'm trying to set up my NIC with a static IP address. The problem is that the machine starts up fine, but eth0 is nowhere to be found. 

Here's my /etc/networking/interfaces:

[INDENT]auto lo
iface lo inet loopback

iface eth0 inet static
address 10.10.0.10
netmask 255.255.255.0
broadcast 10.10.0.255
gateway 10.10.0.254
[/INDENT]The numbers are definitely good, because even though the network is dead on startup, I'm able to kickstart it with the following script:
[INDENT]ifconfig eth0 10.10.0.10 netmask 255.255.255.0 broadcast 10.10.0.255
route add default gw 10.10.0.254
[/INDENT]Nameservers are fine, I put them under /etc/resolve.conf

/var/log/syslog is a little noisy, and I'm not sure what I'm looking for. Nothing is screaming "eth0 error!!!".

Any hints?

---

### Post by arky on 2009-08-13
Add eth0 to auto line to start eth0 on system startup

auto lo eth0

---

### Post by Mxoen on 2009-08-13
D'oh! That is it, alright. I should have caught that one. 

Many thanks!

---

