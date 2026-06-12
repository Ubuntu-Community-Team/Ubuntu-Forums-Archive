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

### Post by Dangertux on 2011-07-15
> **shamora said:**
> hi guys!
I was searching few days for a solution to my problem but haven't found one or I'm too dumb to understand.
Here's what happened:
I have a linux server used as a router. It has an eth0 and eth1 (local interface). I just installed openvpn (I need it only as a client), I configured it and run it. It connects very good the the vpn server but I don't know how to configure iptables so I can connect via tun only from an ip from the local network and all the others to connect normally to my external interface (eth0).
I have tried the following command:
 

 
which works very good except that all the traffic is forwarded thru tun0.
when I put -s 192.168.1.12 (my local ip), also works fine but all the other computers from the network dont have internet access.
let's say my server external ip is A.A.A.A, my local server ip is B.B.B.B and my tun ip is C.C.C.C
how can I create a rule in order to make all ips (except one) to connect thru real ip A.A.A.A to the internet and my ip to connect thru tun ip C.C.C.C ?
I don't seem to find an answer to that or as I said already I'm too dumb.
Any help would be appreciated. 
Thanks guys.

The easiest method I can think of is defining specific rules for each range of ip's. This will take some planning in how you assign ip addresses, but it's the easiest way.

for instance -s 192.168.1.12:20 would allow 12-20, then create a separate rule to send traffic from wherever else to where you want.

---

### Post by shamora on 2011-07-15
I have dhcp enabled on server and only on my computer there is a static ip which I wanna forward through vpn, all the others should connect directly to eth0 and ignore the tun ip. with the quoted command I managed to do that except that all the others just dont connect to the internet. and one more thing ... when I establish the vpn connection also cannot connect outside from the server console. tried mtr, ping, traceroute and so on. I guess I have to change some route & iptables rules but I dont have any idea which and how

---

