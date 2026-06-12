---
title: "First Post - Need help with PPTPD and NAT"
date: 2009-06-17
forum: Networking &amp; Wireless
---

### Post by markytheone on 2009-06-17
Hi guys, firstly hello. I have been using Ubunutu now for a few years and I must say its the best distro I have found so far.

I am running PPTPD (poptop) and installed it using apt-get install pptpd.

I have a couple of problems. Firstly pptpd ignores my localip and remoteip options in my config file at /etc/pptpd.conf.

Secondly once I have connected a PPP session with the server (pings etc all work fine) I cant access the Internet. The server I am connecting to has 1 physical NIC (renamed as eth1).

I want the box to nat any PPTP clients and send them back out over the same interface to the default gateway.

Any advise would be greatly appreciated.

Thanks guys!

Mark

---

### Post by puppywhacker on 2009-06-17
first set up a nat like normal

```
iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
sysctl -w net.ipv4.conf.all.forwarding=1
iptables-save

```
next you have to make sure that you routing is correct on all the machines involved. So when you connect the tunnel you have to make sure your default gateway is still towards the internet. and your pptp client should know that the pptp server is it's default gateway out of there. if you need more assistance post your routing rules after you established the pptp tunnel

and I agree Ubuntu is great =)

---

