---
title: "Limit VPN traffic"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by turixx on 2010-04-02
Hi to everyone!

I have ubuntu server with PPTP on it. I need to limit single connection speed for ip 1 mbit/s, and mounthly traffic limit to 5 GB. How i can do this my task. I try to find somthing with ip tables, but can't find how to creat mounthly limits.PPTP do not have this option, maybe is some other, not hard for configure VPN server? Maybe someone make this task with iptables, and can give commands for limiting? Ofcorse VPN program with integrated accaunts and limits will be better.

Thakall!

---

### Post by wareagle1960 on 2010-04-08
don't know your setup but i have been doing alot of work with iptables as of late this is what i have come up with if you only want to limit speed of a connection (ip address) this seems to work the best in my senario.
 
tc qdisc del dev eth0 root
tc qdisc add dev eth0 root handle 1:0 htb
tc class add dev eth0 parent 1:0 classid 1:1 htb rate 1100kbit
tc qdisc del dev eth1 root
tc qdisc add dev eth1 root handle 1:0 htb
tc class add dev eth1 parent 1:0 classid 1:1 htb rate 1100kbit
tc class add dev eth0 parent 1:1 classid 1:2 htb rate 512kbit ceil 512kbit
tc qdisc add dev eth0 parent 1:2 handle 3: sfq perturb 10
tc class add dev eth1 parent 1:1 classid 1:2 htb rate 512kbit ceil 512kbit
tc qdisc add dev eth1 parent 1:2 handle 3: sfq perturb 10
iptables -t mangle -A POSTROUTING --dst xxx.xxx.xxx.xxx -o eth1 -j CLASSIFY --set-class 1:2
iptables -t mangle -A FORWARD --src xxx.xxx.xxx.xxx -o eth0 -j CLASSIFY --set-class 1:2
 
what this will do is setup a qdisc with resonable defaults to limit traffic on each interface.  eth0 = outside interface and eth1 = inside (download) interface.
xxx......... equals the ip you want to control. 
 
adjust your speeds to you circut.

---

