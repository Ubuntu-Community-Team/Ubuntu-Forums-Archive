---
title: "HELP! Forward VNC IPtables"
date: 2009-03-30
forum: Networking &amp; Wireless
---

### Post by sanemanmad on 2009-03-30
Hello All, 

Here the issue. I am running a gateway, which is running IPtables and transparent proxy (Squid). what I want to do is forward various ports out to other machines behind my gateway.

Short example:
  eth0 (Internet)
   |
Gateway
   |
 bond0 (LAN)
   |
192.168.51.12:5912 (IP: Port I need to forward).

***Before other people start offer solutions, please keep in mind I am not worried about security, otherwise I would just tunnel over SSH and not have this problem :)

Here is my current IPtables script:
```
[SIZE="2"][SIZE="1"]#!/bin/bash
IPT="/sbin/iptables"
INTERNET="eth0"
LAN="bond0"
NETWORK="192.168.51.0/24"
PROXY="192.168.51.10:3128"
$IPT -F
$IPT -F INPUT
$IPT -F OUTPUT
$IPT -F FORWARD
$IPT -F -t mangle
$IPT -F -t nat
$IPT -X
$IPT -P INPUT DROP
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT
#MY ATTEMPT TO FORWARD VNC -- PORT 5912
$IPT -A INPUT -i $INTERNET -s 0/0 -d 0/0 -p tcp --dport 5912 -j ACCEPT
$IPT -t nat -A PREROUTING -i $INTERNET -p tcp --dport 5912 -j DNAT --to 192.168.51.12:5912
#ACCEPT EXISTING CONNECTIONS AND DROP NON-INITIATED
$IPT -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
$IPT -A FORWARD -i $INTERNET -m state --state NEW,INVALID -j DROP
#ACCEPT LAN to LAN TRAFFIC
$IPT -A INPUT -i $LAN -s $NETWORK -d $NETWORK -p all -j ACCEPT
#REDIRECT ALL TRAFFIC TO PROXY AND ALLOW ACCESS TO LOCAL WEBSERVER ON PROXY
$IPT -t nat -A PREROUTING -i $LAN -p tcp --dport 80 -d ! 192.168.51.10 -j DNAT --to $PROXY
$IPT -t nat -A PREROUTING -i $INTERNET -p tcp --dport 80 -j REDIRECT --to-port 3128
#NAT
$IPT -t nat -A POSTROUTING -o $INTERNET -j MASQUERADE
#LOGGING
$IPT -N firewall
$IPT -A firewall -m limit --limit 15/minute -j LOG --log-prefix Firewall:
$IPT -A firewall -j DROP
$IPT -N dropwall
$IPT -A dropwall -m limit --limit 15/minute -j LOG --log-prefix Dropwall:
$IPT -A dropwall -j DROP
$IPT -N badflags
$IPT -A badflags -m limit --limit 15/minute -j LOG --log-prefix Badflags:
$IPT -A badflags -j DROP
$IPT -N silent
$IPT -A silent -j DROP
$IPT -A INPUT -i lo -j ACCEPT
#BAD FLAGS
$IPT -A INPUT -p tcp -s 0.0.0.0/0 -m string --string .download?file=%2e%2e. --algo bm -j DROP
$IPT -A INPUT -p tcp --tcp-flags ALL FIN,URG,PSH -j badflags
$IPT -A INPUT -p tcp --tcp-flags ALL ALL -j badflags
$IPT -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j badflags
$IPT -A INPUT -p tcp --tcp-flags ALL NONE -j badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j badflags
$IPT -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j badflags
#PING SETTINGS
$IPT -A INPUT -p icmp --icmp-type 0 -m limit --limit 3/second -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type 3 -m limit --limit 3/second -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type 11 -m limit --limit 3/second -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type 8 -m limit --limit 3/second -j ACCEPT
$IPT -A INPUT -p icmp -j firewall
#ALLOW SSH
$IPT -A INPUT -i $INTERNET -s 0/0 -d 0/0 -p tcp --dport 22 -j ACCEPT
#MODPROBE
modprobe ip_conntrack
modprobe ip_conntrack_ftp
echo 1 > /proc/sys/net/ipv4/ip_forward
echo 1 > /proc/sys/net/ipv4/tcp_syncookies
$IPT -A INPUT -j LOG --log-prefix "Drop Packets: "
$IPT -A INPUT -j DROP[/SIZE][/SIZE]

```

Whenever I attempt to connect over internet via real.ip: port it says the connection timed out, However I am currently ssh into my machine and am able to tunnel VNC that way. So in short I know it is has to be an error in my firewall script

---

### Post by coutts99 on 2009-03-30
Is iptables reporting that it is blocking it?

---

### Post by sanemanmad on 2009-03-30
> **coutts99 said:**
> Is iptables reporting that it is blocking it?

I am new to IPtables... Can I get this information from the syslog?

---

### Post by coutts99 on 2009-03-30
Yes but not sure where, mine just show up when I do a dmesg

---

### Post by sanemanmad on 2009-03-30
Hmm... It does not show any packets dropped from that port or my IP? Weird I can ftp and SSH no problem.


This is the last n lines or so, immediately after attempting VNC
```
[SIZE="1"]dmesg|grep -i "Drop Packets: IN=eth0"
00 PREC=0x00 TTL=255 ID=5060 PROTO=UDP SPT=67 DPT=68 LEN=402
[235284.641728] Drop Packets: IN=eth0 OUT= MAC=00:09:5b:06:b7:4b:00:12:d9:54:5b:cf:08:00 SRC=151.59.131.244 DST=68.3.60.106 LEN=48 TOS=0x00 PREC=0x00 TTL=114 ID=20837 DF PROTO=TCP SPT=1806 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0
[235284.651430] Drop Packets: IN=eth0 OUT= MAC=00:09:5b:06:b7:4b:00:12:d9:54:5b:cf:08:00 SRC=76.66.27.129 DST=68.3.60.106 LEN=48 TOS=0x00 PREC=0x00 TTL=52 ID=22584 DF PROTO=TCP SPT=61105 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0
[235285.480303] Drop Packets: IN=eth0 OUT= MAC=00:09:5b:06:b7:4b:00:12:d9:54:5b:cf:08:00 SRC=70.75.61.163 DST=68.3.60.106 LEN=48 TOS=0x00 PREC=0x00 TTL=116 ID=53124 DF PROTO=TCP SPT=61883 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0
[235285.584734] Drop Packets: IN=eth0 OUT= MAC=00:09:5b:06:b7:4b:00:12:d9:54:5b:cf:08:00 SRC=84.72.32.153 DST=68.3.60.106 LEN=48 TOS=0x00 PREC=0x00 TTL=51 ID=41456 DF PROTO=TCP SPT=61310 DPT=51413 WINDOW=65535 RES=0x00 SYN URGP=0
[235285.672977] Drop Packets: IN=eth0 OUT= MAC=00:09:5b:06:b7:4b:00:12:d9:54:5b:cf:08:00 SRC=90.148.245.244 DST=68.3.60.106 LEN=95 TOS=0x00 PREC=0x00 TTL=115 ID=18469 PROTO=UDP SPT=15629 DPT=51413 LEN=75[/SIZE]
```

---

### Post by jbrevik on 2009-03-30
Just curious but I noticed you used 5912 as the VNC port. Is this correct? Did you change the VNC port to 5912? If not, the default port should be 5900.

---

### Post by sanemanmad on 2009-03-30
Yes, I changed the default port to match the ending ip of each host.









I'm in Phoenix too :P

---

### Post by sanemanmad on 2009-04-05
I was able to get it working. Thanks.

```
$IPT -t nat -A PREROUTING -i $INT -p tcp --dport 5912 -j DNAT --to 192.168.51.12:5912
```

That was easy...

---

