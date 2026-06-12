---
title: "Multiple ISP Connections on Ubuntu Server Firewall"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by compucoder on 2009-02-03
Hi everyone,

I am using Ubuntu 8.10 Server which is a dedicated firewall perimeter box.

I just got our second internet connection setup today and am having trouble getting it to co-exist with the first provider.

I want to route most of the LAN through ISP1 and 3 clients on the same LAN through the other.

I can't even get to point of making the shorewall rules to do this as I can't get the second ISP to work on the firewall. I did test it using a laptop and know it works. Here is what I have done so far:

eth1 is ISP1, eth2 is ISP2 and eth0 is the LAN. (I fudged my IP's a bit for security sakes)

In my /etc/network/interfaces file I have this:

# The loopback network interface
auto lo eth1 eth2 eth0
iface lo inet loopback


iface eth1 inet static
address 111.11.111.154
netmask 255.255.255.248
network 111.11.111.152
broadcast 111.11.111.159
dns-nameservers 111.11.2.133 111.11.2.36
gateway 111.11.111.153

iface eth2 inet static
address 222.22.222.194
netmask 255.255.255.248
network 222.22.222.192
broadcast 222.22.222.199
dns-nameservers 222.22.23.114
gateway 222.22.222.193


iface eth0 inet static
address 192.168.1.1
netmask 255.255.255.0
broadcast 192.168.1.255
network 192.168.1.0

I tried commenting out gateway in eth2 and that got eth1 working again. When I did the above with 2 gateways none worked.

I have read the great article on multiple providers from LARTC but it is using low level calls directly like ip route add . I am trying to do this within the confines of Ubuntu's config files. I also don't see why everything stopped working when I had a gateway defined for eth1 and eth2.

I use shorewall for my firewall config and currently use MASQ to NAT eth0 to eth1. I am sure I'll have to add more rules, zones and MASQ entries to route the 3 clients on the LAN through ISP 2. I have to get the networking stuff working first which is my first hurdle.

If anyone can see what I am doing wrong above, what else I should be doing, etc. I would really appreciate the help.

Oh, I should also mention I use webmin to configure my interfaces / shorewall, etc. if that matters. I am sure it is doing stuff for me I don't know about that may be the cause of my troubles. I noticed the routes page has both networks listed yet I didn't explicitly set them. I assume either webmin did this for me or the Linux networking system figures this out itself based on the settings in my interaces file above... not sure.

Thanks.

---

