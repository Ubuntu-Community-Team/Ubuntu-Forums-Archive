---
title: "PPTP Server some websites don't load"
date: 2011-06-24
forum: Networking &amp; Wireless
---

### Post by skej on 2011-06-24
Running Ubuntu 11.04 Server 32bit fresh install

I did this [_walk-through_]("http://cviorel.easyblog.ro/2009/02/09/how-to-set-up-a-vpn-server-on-ubuntu/") trying both iptables and ufw

I am able to connect to my VPN server using both windows 7 and Ubuntu desktop just fine, and using wireshark verify that all packets are being compressed and sent through the VPN tunnel. 

Many sites work but there are several that will not load while using the VPN, one of them is ubuntu forums also sourceforge.

I can ping the servers while connected but the websites just will not load, and time out. The second I disconnect from the VPN they load instantly.

---

### Post by skej on 2011-06-27
Still having the same issue.:(

---

### Post by skej on 2011-11-07
I have just installed 11.10 x86 server as a virtual machine and configured to be a PPTP VPN server to see if this issue still exists and it does =( I can access some websites others not at all, for instance [www.vmware.com](www.vmware.com) or the ubuntu forums will not load at all.

---

### Post by karentom on 2011-12-21
Hy. I can confirm this. I have same or very similar issue with Ubuntu 10.04 as a VPN server PPTP connection. I have no clue what is it.
Have you found something yet?

---

### Post by sabaitechnology on 2012-06-09
I have been working on this issue and came up with two different fixes I  needed on our setup.  First, the description of the issue:  Many  websites were loading but some just wouldn't load. 

Some sites affected were:

speedtest.net
paypal.com
scottys.com
ubuntuforums.org

The first issue we had was that we had not set ip_forward and ip_dynaddr properly.  That was fixed with the following:

echo "1" > /proc/sys/net/ipv4/ip_forward
echo "1" > /proc/sys/net/ipv4/ip_dynaddr 

When  I did this, speedtest.net and scottys.com started working but  paypal.com was still broken.  This was due to a mtu issue over the pptp  which was resolved with the following.

iptables -I FORWARD -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

This line should help set things up properly to get the websites flowing again.  Hope this helps!

---

