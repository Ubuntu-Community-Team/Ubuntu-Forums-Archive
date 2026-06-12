---
title: "squid3 transparent proxy using wccp"
date: 2011-11-23
forum: Networking &amp; Wireless
---

### Post by terminator14 on 2011-11-23
I work for a small ISP that provides internet for a few thousand people, and lately I've been trying to get a squid web cache server to work on our network in order to speed up our users' web page load times. The problem is - I've never worked with squid before, and after a few days of trying to set it up, I'm pretty close to pulling my hair out.

This is as far as I got, using about 20 different articles online at the same time, as well as a book on squid:

**Configure Cisco:**

ip wccp web-cache redirect-list test group-list 10
int Gi0
[COLOR="White"].[/COLOR]  ip wccp web-cache redirect in

ip access-list test
    10 deny ip host 10.10.10.2 any
    20 permit tcp host 192.168.13.250 any eq www
    30 deny ip any any

ip access-list 10
    10 permit 10.10.10.2


**Configure Squid on Linux:**

sudo apt-get install squid3
sudo vim /etc/squid3/squid.conf

Changes made from default -

acl My_Network src 192.168.13.0/24
http_access allow My_Network
http_port 3128 transparent
cache_dir ufs /var/spool/squid3 180000 16 256
wccp2_router 10.10.10.1
wccp_version 4
wccp2_forwarding_method gre
wccp2_return_method gre
wccp2_service standard 0

**Configure Linux OS itself:**

/sbin/ip tunnel add wccp1 mode gre remote 10.10.10.1 local 127.0.0.2 dev eth0
/sbin/ip link set wccp1 mtu 1476
/sbin/ip addr add 127.0.0.2 dev wccp1
/sbin/ip link set wccp1 up
/sbin/sysctl -w net.ipv4.conf.wccp1.rp_filter=0
/sbin/sysctl -w net.ipv4.conf.eth0.rp_filter=0

sudo iptables -t nat -A PREROUTING -s 10.10.10.2 -p tcp --dport 80 -j ACCEPT
sudo iptables -t nat -A PREROUTING -p tcp --dport 80 -j DNAT --to-destination 10.10.10.2:3128
sudo iptables -t nat -A POSTROUTING -j MASQUERADE

echo 1 > /proc/sys/net/ipv4/ip_forward
echo 0 > /proc/sys/net/ipv4/conf/default/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/all/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/eth0/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/lo/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/wccp1/rp_filter

Notes: The Cisco router is running ACLs (firewall) but the machines in question are currently exempt from it (all traffic from and to these machines is allowed).

When I run the squid service (sudo service squid3 start), squid registers with the router using wccp, and the router starts redirecting all packets destined to port 80 from 192.168.13.250 to squid. This results in that machine, and only that machine loosing it's ability to surf the web because something is broken on the squid machine. Once I turn off the squid service, the router detects that it is gone and stops forwarding traffic to squid, so I get my web browsing back.

tshark reveals that packets are being received from 192.168.13.250 on the eth0 interface of the squid machine.

iptables -t nat -nvL however shows that NO packets were redirected to port 3128 (no packets hit that rule).

Do I have bad iptables rules? Did I use a wrong IP on the gre tunnel interface (wccp1)? Did I do something else wrong?

Any help would be greatly appreciated.

---

### Post by terminator14 on 2011-11-24
I'm fairly confident that the problem is either the iptables rules or the GRE tunnel. Anyone have any idea what it could be? Even if you don't know the problem but can confirm that one of those 2 things is as it should be, that would be really helpful.

---

### Post by terminator14 on 2012-05-08
Ok so after failing at the task above, and putting it off for a while as more important things came up, I finally got back to trying this again.

The task is still basically the same - getting WCCP and squid to work together.

I'm pretty sure my Cisco router is configured properly. I'm pretty sure squid.conf is configured properly. The Cisco router ACL is NOT blocking anything coming from or going to the squid server. The linux firewall (iptables) is also NOT blocking anything. 'show ip wccp' on the router shows that squid registers with the router, and wireshark on the squid server shows that the GRE tunnel is receiving packets. The iptables rule that is meant to redirect all traffic from the GRE tunnel to the squid port shows that it's getting hits now (iptables -t nat -nvL PREROUTING). The thing is - squid logs don't show that it's receiving any kind of requests. The test machine (the only machine that WCCP should be sending HTTP traffic to squid from) basically can't load any web page once the squid daemon is started on the squid server. Is there something wrong with the iptables rule? Could it be something else? Here are the different sections:

**Router:**
```


ip wccp web-cache redirect-list 120 group-list 10

interface GigabitEthernet0/2
 ip wccp web-cache redirect in

ip access-list standard 10
 permit [squid server IP]

ip access-list extended 120
 deny   ip host [squid server IP] any
 permit tcp host [test machine] any eq www
 deny   ip any any

```

**Squid server:**

```

iptunnel add gre1 mode gre remote [external IP of router] local [squid server IP] dev eth0
ip addr add [squid server IP]/32 dev gre1
ip link set gre1 up

echo 1 > /proc/sys/net/ipv4/ip_forward
echo 0 > /proc/sys/net/ipv4/conf/default/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/all/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/eth0/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/lo/rp_filter
echo 0 > /proc/sys/net/ipv4/conf/gre1/rp_filter
iptables -t nat -A PREROUTING -i gre1 -p tcp -m tcp --dport 80 -j DNAT --to-destination [squid server ip]:3128
```

**squid.conf:**

```
acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl localnet src [network test machine is on]
acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localnet
http_access allow localhost
http_access deny all
http_port 3128 transparent
hierarchy_stoplist cgi-bin ?
coredump_dir /var/spool/squid
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern -i (/cgi-bin/|\?) 0	0%	0
refresh_pattern .		0	20%	4320
wccp2_router [IP of router]
wccp_version 4
wccp2_forwarding_method gre
wccp2_return_method gre
wccp2_service standard 0

```

I know this is not a simple question, but I'm pretty sure it's a simple answer (if I could only see it). If you have any experience setting up WCCP with squid, please give the above config files a quick look. I practically have no more hair to pull out.

---

### Post by terminator14 on 2012-06-08
Wow! After weeks of trying to get this to work (on and off), and reading every howto on google relating to wccp and squid, I finally came across a line on some website that read:

> For Squid to work with WCCP2 and the Cisco firewall, the Squid server must be on a common subnet with the web client...

As soon as I made this happen, everything finally started working. I knew it was something simple.

---

