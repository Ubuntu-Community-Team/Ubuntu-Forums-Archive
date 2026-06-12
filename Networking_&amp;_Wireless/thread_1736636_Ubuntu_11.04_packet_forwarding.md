---
title: "Ubuntu 11.04 packet forwarding"
date: 2011-04-22
forum: Networking &amp; Wireless
---

### Post by asmfc23 on 2011-04-22
Hi,

I feel like an epic noob here, but I have invested quite some time in looking into this, so I should now admit failure and exit denial at last :)

I have a U11.04 box with two interfaces - an ethernet dhcp-configured WAN interface and an AR9285 access point. I have configured the AP using hostapd. 

Hostapd creates a mon.wlan0 interface, I have set the IP on the wlan0 interface, setup dhcpd, etc.

The issue comes when configuring the iptables to NAT the traffic (or when configuring the kernel to route it from the one interface to the other?)

I have used the following to configure the AP:

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
iptables --append FORWARD --in-interface wlan0 -j ACCEPT

To be on the safe side - and I know it is not neccessary I have set this opition in /etc/sysctl.conf up:
net.ipv4.ip_forward = 1

Still, when I try pinging from the box with source address the wlan0 interface, I fail with "Destination Host Unreachable" from the wlan0 interface (the packets are not routed to the eth0).

Can anyone throw me a bone here?

---

### Post by josephmills on 2011-04-22
> **asmfc23 said:**
> Hi,

I feel like an epic noob here, but I have invested quite some time in looking into this, so I should now admit failure and exit denial at last :)

I have a U11.04 box with two interfaces - an ethernet dhcp-configured WAN interface and an AR9285 access point. I have configured the AP using hostapd. 

Hostapd creates a mon.wlan0 interface, I have set the IP on the wlan0 interface, setup dhcpd, etc.

The issue comes when configuring the iptables to NAT the traffic (or when configuring the kernel to route it from the one interface to the other?)

I have used the following to configure the AP:

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
iptables --append FORWARD --in-interface wlan0 -j ACCEPT

To be on the safe side - and I know it is not neccessary I have set this opition in /etc/sysctl.conf up:
net.ipv4.ip_forward = 1

Still, when I try pinging from the box with source address the wlan0 interface, I fail with "Destination Host Unreachable" from the wlan0 interface (the packets are not routed to the eth0).

Can anyone throw me a bone here?

I have no clue but have you tried replaceing hostapd with aircrack-ng?

---

### Post by asmfc23 on 2011-04-22
> **josephmills said:**
> I have no clue but have you tried replaceing hostapd with aircrack-ng?

Hello,

Thanks for trying to help.
aircrack-ng is a tool for password cracking, however, not a software for AP creation.

Cheers!

---

### Post by Danimoth on 2011-04-26
> **asmfc23 said:**
> 
To be on the safe side - and I know it is not neccessary I have set this opition in /etc/sysctl.conf up:
net.ipv4.ip_forward = 1



Just tried this and you are right! You do not have to uncomment that line.
I am not sure why this is the case, I always thought this was a necessary step. Can you explain why it is not necessary or point me to where you found the info?
:)


About your issue:
[I usually configure my firewall/router with fwbuilder which may automatically configure some things, so hopefully I won't confuse the situation even more. ]
1) Do you really need to NAT your traffic? If this is just your local network, then I think that you need to configure the routing table. I used this documentation: 
[http://linux-ip.net/html/routing-tables.html](http://linux-ip.net/html/routing-tables.html)

2) Are the IPs issued on the 2 interfaces on the same subnet? Try assigning a separate subnet for the AP. eg: 

```

LAN: 
192.168.1.128/25 which is the same as 192.168.1.128/255.255.255.128 
IPs to use: 192.168.1.129-192.168.1.254
(in this case: Network = 192.168.1.128, Broadcast = 192.168.1.255)

WLAN:
192.168.1.0/25 which is the same as 192.168.1.0/255.255.255.128
IPs to use: 192.168.1.1-192.168.1.126
(in this case: Network = 192.168.1.0, Broadcast = 192.168.1.127 )

```


EDIT: **Another idea is to bridge the two interfaces. This is probably the first thing you should try.**

---

### Post by asmfc23 on 2011-04-26
Hi,

> **Danimoth said:**
> Just tried this and you are right! You do not have to uncomment that line.
I am not sure why this is the case, I always thought this was a necessary step. Can you explain why it is not necessary or point me to where you found the info?
:)


Well, it is the same configuration item, only you can configure it on two places - and it gets loaded at different times. If you use sysctl (or edit manually the conf file), the kernel gets loaded with this option. Otherwise, if you use the /proc/sys file, the option gets enabled once the interfaces are initiated. In most cases, it does not matter what you use. I do not have any links, I know this for ages now.


> **Danimoth said:**
> 
1) Do you really need to NAT your traffic? If this is just your local network, then I think that you need to configure the routing table. I used this documentation: 
[http://linux-ip.net/html/routing-tables.html](http://linux-ip.net/html/routing-tables.html)


Yes, I do. I am really good at shortcutting, but this is not an option here. Some ASCII topology:

ISP <---> eth0|wlan0 <---> LAN

My ISP uses on-demand DHCP-to-MAC-bindings + MAC filtering, so I cannot bridge. Additionally, if I do, I will not be able to access the Internet from the Linux box.

> **Danimoth said:**
> 
2) Are the IPs issued on the 2 interfaces on the same subnet? Try assigning a separate subnet for the AP. eg: 


definitely not. I have a routable IP address on eth0 and a private IP (192.168.5.1/24) setup on wlan0.

In the meantime, I have this up and running using Scientific Linux.  I had to recompile the kernel and the atheros drivers ~20 times :)

I will retry this setup once the 11.04 gets officially released.

---

### Post by handsomex on 2011-09-26
I have same configurations to you ubuntu 11.04 and meet same problems. I can't figure out what's wrong :(. I did this on 10.04 several times. Never met this before :(

---

### Post by handsomex on 2011-09-26
after several reboots, it works magically :( do not know why :( however sometimes it stops working for no reason. simply restart it :(

---

