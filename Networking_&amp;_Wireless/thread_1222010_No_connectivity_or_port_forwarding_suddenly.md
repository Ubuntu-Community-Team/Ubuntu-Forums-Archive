---
title: "No connectivity or port forwarding suddenly"
date: 2009-07-24
forum: Networking &amp; Wireless
---

### Post by lacc4hope on 2009-07-24
Hello,
 
I have an Xubuntu system I am using for loadbalancing and routing.
 
I used the following generic script for NAT/port forwarding:
 
**echo 1 > /proc/sys/net/ipv4/ip_forward**
 
**/sbin/iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE**
 
 
**/sbin/iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT**
 
**/sbin/iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT**
 
Mine was tailored to our scenario, in which I am forwarding from 3 interfaces (WAN) to 1 interface (LAN).
 
This stopped working suddenly after a reboot. After checking a few things out and a second reboot, I lost all network connectivity in addition to port forwarding.
 
I was never able to get this to work in my rc.local, so this was entered manually after any reboot on the machine. Also, I am using 4 identical model 3com NICs (3c5CX's).
 
Any ideas? Is Xubuntu a poor distro to use for this kind of thing? I'm new to the Linux world, I don't know.

---

### Post by lacc4hope on 2009-07-25
Nobody has any troubleshooting ideas for this?

---

