---
title: "Ubuntu Server 10.10 as router. Work all except google"
date: 2010-11-29
forum: Networking &amp; Wireless
---

### Post by AnatolyZ on 2010-11-29
Hi all,

Please help with ubuntu-based router settings. Currently I can acces any site in Internet from any machine in our LAN. Except [www.google.com!!!!Moreover](www.google.com!!!!Moreover) I can access even google subdomains (i.e. translate.google.com) thru the router. But google.com page is not loaded.

I installed Ubuntu Server 10.10 to the router. Internet interface is PPPoE. To share internet i did the following:

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -A FORWARD -i $lan -o $wan -j ACCEPT
iptables -A FORWARD -i $wan -o $lan -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

iptables -t nat -A POSTROUTING -o $wan -s 192.168.0.0/24 -j MASQUERADE



cat provider:

noipdefault
#nodefaultroute
defaultroute
replacedefaultroute
hide-password
lcp-echo-interval 20   
lcp-echo-failure 3
noauth
#mtu 1492
persist
maxfail 0
holdoff 15
plugin rp-pppoe.so
nic-mega
user "6104"
usepeerdns
unit 1
noproxyarp

---

### Post by AnatolyZ on 2010-11-29
On clients I set DNS to OpenDNS or to my ISP's DNS.


ISP does not block [www.google.com](www.google.com) becaus if I replace ubuntu-router with Dlink router all work ok.

---

### Post by AnatolyZ on 2010-11-30
Solved with:

iptables -t mangle -A FORWARD -p tcp -m tcp --tcp-flags RST,SYN SYN -j TCPMSS --clamp-mss-to-pmtu

This is a very ofter problem for pppoe. Please google for explanation (I have link only on own language)

---

