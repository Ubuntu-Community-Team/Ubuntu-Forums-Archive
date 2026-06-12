---
title: "Iptables script"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by braiamp on 2009-08-20
Hello.
 
This is my first post in this forum.
 
As said on the title, I generate an a automatic script to set my iptables rules but for some reason it thosent work.
 
I atach a flush of the script.
 
Any help are welcome.
 
PS: My english is limited, my contry language is spanish.

---

### Post by Brandon Williams on 2009-08-22
That's a pretty long script with a lot going on. It would be better if you could be specific about what doesn't work. Does the script display errors when you run it? Do you end up with any of the expected rules?

---

### Post by braiamp on 2009-08-24
I kwon it, that´s is soo looong.
 
But, the important thing is that, it finish with unexpected exit, and iptables block everything. I don´t know if is the rule or the error that made iptables block anythink.

---

### Post by braiamp on 2009-08-24
> **braiamp said:**
> I kwon it, that´s is soo looong.
 
But, the important thing is that, it finish with unexpected exit, and iptables block everything. I don´t know if is the rule or the error that made iptables block anythink.
 
If you know about another place when I can generate a iptables scrip that allow Start-stop in init.d I´ll thank you.

---

### Post by braiamp on 2010-01-05
> **braiamp said:**
> If you know about another place when I can generate a iptables scrip that allow Start-stop in init.d I´ll thank you.
 
I run one by one the rules and then, I've installed a modificated version of a init scrip that run on Gentoo that save my iptables rules at shutdown and reload it at startup.
 
I flush my iptables rules and where i get the script
 
[http://ubuntuforums.org/showthread.php?t=19106](http://ubuntuforums.org/showthread.php?t=19106)
 
```
-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-N bad_packets
-N bad_tcp_packets
-N icmp_packets
-N tcp_inbound
-N tcp_outbound
-N udp_inbound
-N udp_outbound
-A INPUT -i lo -j ACCEPT
-A INPUT -j bad_packets
-A INPUT -d 224.0.0.1/32 -j DROP
-A INPUT -s 192.168.2.0/24 -i eth1 -j ACCEPT
-A INPUT -d 192.168.2.255/32 -i eth1 -j ACCEPT
-A INPUT -i eth1 -p udp -m udp --sport 68 --dport 67 -j ACCEPT
-A INPUT -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -i eth0 -p tcp -j tcp_inbound
-A INPUT -i eth0 -p udp -j udp_inbound
-A INPUT -i eth0 -p icmp -j icmp_packets
-A INPUT -m pkttype --pkt-type broadcast -j DROP
-A INPUT -j LOG --log-prefix "fp=INPUT:99 a=DROP "
-A FORWARD -j bad_packets
-A FORWARD -i eth1 -p tcp -j tcp_outbound
-A FORWARD -i eth1 -p udp -j udp_outbound
-A FORWARD -i eth1 -j ACCEPT
-A FORWARD -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -d 192.168.2.5/32 -i eth0 -p udp -m udp --dport 19118 -j ACCEPT
-A FORWARD -d 192.168.2.5/32 -i eth0 -p tcp -m tcp --dport 19118 -j ACCEPT
-A FORWARD -j LOG --log-prefix "fp=FORWARD:99 a=DROP "
-A OUTPUT -p icmp -m state --state INVALID -j DROP
-A OUTPUT -s 127.0.0.1/32 -j ACCEPT
-A OUTPUT -o lo -j ACCEPT
-A OUTPUT -s 192.168.2.1/32 -j ACCEPT
-A OUTPUT -o eth1 -j ACCEPT
-A OUTPUT -o eth0 -j ACCEPT
-A OUTPUT -j LOG --log-prefix "fp=OUTPUT:99 a=DROP "
-A bad_packets -s 192.168.2.0/24 -i eth0 -j LOG --log-prefix "fp=bad_packets:2 a=DROP "
-A bad_packets -s 192.168.2.0/24 -i eth0 -j DROP
-A bad_packets -m state --state INVALID -j LOG --log-prefix "fp=bad_packets:1 a=DROP "
-A bad_packets -m state --state INVALID -j DROP
-A bad_packets -p tcp -j bad_tcp_packets
-A bad_packets -j RETURN
-A bad_tcp_packets -i eth1 -p tcp -j RETURN
-A bad_tcp_packets -i eth1 -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j DROP
-A bad_tcp_packets -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j LOG --log-prefix "fp=bad_tcp_packets:1 a=DROP "
-A bad_tcp_packets -p tcp -m tcp ! --tcp-flags FIN,SYN,RST,ACK SYN -m state --state NEW -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j LOG --log-prefix "fp=bad_tcp_packets:2 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG NONE -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,PSH,ACK,URG -j LOG --log-prefix "fp=bad_tcp_packets:3 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,PSH,ACK,URG -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j LOG --log-prefix "fp=bad_tcp_packets:4 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,PSH,URG -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,ACK,URG -j LOG --log-prefix "fp=bad_tcp_packets:5 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN,RST,PSH,ACK,URG FIN,SYN,RST,ACK,URG -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j LOG --log-prefix "fp=bad_tcp_packets:6 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags SYN,RST SYN,RST -j DROP
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j LOG --log-prefix "fp=bad_tcp_packets:7 a=DROP "
-A bad_tcp_packets -p tcp -m tcp --tcp-flags FIN,SYN FIN,SYN -j DROP
-A bad_tcp_packets -p tcp -j RETURN
-A icmp_packets -p icmp -f -j LOG --log-prefix "fp=icmp_packets:1 a=DROP "
-A icmp_packets -p icmp -f -j DROP
-A icmp_packets -p icmp -m icmp --icmp-type 8 -j LOG --log-prefix "fp=icmp_packets:2 a=ACCEPT "
-A icmp_packets -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A icmp_packets -p icmp -m icmp --icmp-type 8 -j DROP
-A icmp_packets -p icmp -m icmp --icmp-type 11 -j ACCEPT
-A icmp_packets -p icmp -j RETURN
-A tcp_inbound -p tcp -m tcp --dport 113 -j REJECT --reject-with icmp-port-unreachable
-A tcp_inbound -p tcp -m tcp --dport 80 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 443 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 21 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --sport 20 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 62000:64000 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 5000:5100 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 6891:6900 -j ACCEPT
-A tcp_inbound -p tcp -m tcp --dport 2222:5500 -j ACCEPT
-A tcp_inbound -p tcp -j RETURN
-A tcp_outbound -p tcp -j ACCEPT
-A udp_inbound -p udp -m udp --dport 137 -j DROP
-A udp_inbound -p udp -m udp --dport 138 -j DROP
-A udp_inbound -p udp -m udp --dport 113 -j REJECT --reject-with icmp-port-unreachable
-A udp_inbound -p udp -m udp --dport 123 -j ACCEPT
-A udp_inbound -p udp -m udp --dport 53 -j ACCEPT
-A udp_inbound -p udp -m udp --sport 53 -j ACCEPT
-A udp_inbound -p udp -m udp --dport 2222:5500 -j ACCEPT
-A udp_inbound -p udp -j RETURN
-A udp_outbound -p udp -j ACCEPT

```

---

