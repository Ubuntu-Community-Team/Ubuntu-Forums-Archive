---
title: "IPv6 sysctl problems"
date: 2012-06-09
forum: Networking &amp; Wireless
---

### Post by wsteffen on 2012-06-09
I am working on getting a xubuntu based router/firewall setup behind a cable modem connected to my ISP. IPv4 works fine. I have the following lines in /etc/sysctl.conf
net.ipv6.conf.eth1.forwarding=1
net.ipv6.conf.eth1..accept_ra=0
net.ipv6.conf.eth0.forwarding=1
net.ipv6.conf.eth0..accept_ra=2

And in in /etc/network/interfaces file there is the following:
auto eth0
iface eth0 inet dhcp
iface eth0 inet6 dhcp

(eth1 config)

eth0 is the modem interface. If I boot with this config, 
/proc/sys/net/ipv6/conf/eth0/accept_ra is equal to 0
If i comment out "iface eth0 inet6 dhcp" in the interfaces file, then /proc/sys/net/ipv6/conf/eth0/accept_ra is equal to 2.
Can anyone explain this? I want to configure eth0 IPv6 address using dhcp along with DNS etc, and still get router advertisements.
It is my opinion that parameters set in /etc/sysctl should be used as they are set.

HELP

---

### Post by ratcheer on 2012-06-09
It looks like you are trying to do the things I want to learn how to do in the near future. I wish I could help you, but you have already advanced beyond me. The main suggestion I could offer is, why don't you consider a dedicated distro, such as pfSense, Untangle, etc?

I want a low power consumption, small PC with no moving parts, but with the capacity for two NICs. I can almost do everything I need on my Netgear WNDR3300 router flashed with dd-wrt, but it does not have ip6tables and I have used all but 6kb of its small memory capacity.

Anyway, I am interested in how things go for you on your project. Good luck!

Tim

---

### Post by wsteffen on 2012-06-09
I am using a Neoware thin client I got on Ebay. Model CA10 which came with a extra wireless card, which I replaced with an ethernet card.
The distro is xubuntu 11.10 kernel 3.0.0-12-generic with a lot of not-needed software removed.

---

