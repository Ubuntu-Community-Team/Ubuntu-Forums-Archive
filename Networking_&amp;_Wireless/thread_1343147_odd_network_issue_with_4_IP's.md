---
title: "odd network issue with 4 IP's"
date: 2009-12-01
forum: Networking &amp; Wireless
---

### Post by xkaliburx on 2009-12-01
Well our FW died so I replaced with a basic server 2 nic's (2 ports each).  The layout has the following;
eth0 - ISP provided
eth1 - public subnet1
eth2 - public subnet2
eth3 - private management

The first 3 work fine, but the 4th (eth3) has the following issue and needs resolution due to our VPN connection uses that network.

An ifdown/up eth3 shows  
#ifdown eth3
ifdown: interface eth3 not configured

I can change the static IP in the interfaces file, restart and an ifconfig shows that new address.  The other odd thing, as I said, ifconfig shows the IP, but I can't ping it.  I can however ping other devices on that subnet and a route shows that subnet.

I am using this server as the primary firewall and I am wondering also if it could be a routing/iptables type thing why the no reply on pinging himself, but any ideas on the error is appreciated.

---

