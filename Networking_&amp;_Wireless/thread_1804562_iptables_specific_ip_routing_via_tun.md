---
title: "iptables specific ip routing via tun"
date: 2011-07-14
forum: Networking &amp; Wireless
---

### Post by shamora on 2011-07-14
hi guys!
I was searching few days for a solution to my problem but haven't found one or I'm too dumb to understand.
Here's what happened:
I have a linux server used as a router. It has an eth0 and eth1 (local interface). I just installed openvpn (I need it only as a client), I configured it and run it. It connects very good the the vpn server but I don't know how to configure iptables so I can connect via tun only from an ip from the local network and all the others to connect normally to my external interface (eth0).
I have tried the following command:
 
> iptables -t nat -A POSTROUTING -s 192.168.1.0/24 -o tun0 -j MASQUERADE 
 
which works very good except that all the traffic is forwarded thru tun0.
when I put -s 192.168.1.12 (my local ip), also works fine but all the other computers from the network dont have internet access.
let's say my server external ip is A.A.A.A, my local server ip is B.B.B.B and my tun ip is C.C.C.C
how can I create a rule in order to make all ips (except one) to connect thru real ip A.A.A.A to the internet and my ip to connect thru tun ip C.C.C.C ?
I don't seem to find an answer to that or as I said already I'm too dumb.
Any help would be appreciated. 
Thanks guys.

---

