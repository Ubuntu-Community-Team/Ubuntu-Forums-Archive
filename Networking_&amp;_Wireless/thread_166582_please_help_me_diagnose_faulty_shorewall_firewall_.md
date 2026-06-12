---
title: "please help me diagnose faulty shorewall firewall setup"
date: 2006-04-26
forum: Networking &amp; Wireless
---

### Post by stanwebber on 2006-04-26
i only started learning how to use shorewall yesterday.  there is something faulty with this 3 interface firewall i built that i'm just unable to see.  here are the symptoms:

- machines on ath0 & vmnet1 are unable to access the internet
- machines on ath0 & vmnet1 are unable to ping machines on each others' subnet
- firewall machine is able to access the internet & shieldsup port scan shows (at least externally) firewall is functioning as configured
- with shorewall removed, & nat provided by ipmasq, network performs flawlessly (except no firewall)
- i have tried rebooting the firewall machine

perhaps someone more familiar with shorewall will see what i'm missing

zones
```
net	Net		Internet
loc	Local		Local Network
vir	Virtual		Virtual Network
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
```

interfaces
```
net	eth0		detect		dhcp,routefilter,norfc1918
loc	ath0		192.168.0.255
vir	vmnet1		192.168.1.255
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
```

masq
```
eth0			192.168.0.0/24
eth0			192.168.1.0/24
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
```

policy
```
loc		net		ACCEPT
vir		net		ACCEPT
# If you want open access to the Internet from your Firewall 
# remove the comment from the following line.
fw		net		ACCEPT
net		all		DROP		info
# THE FOLLOWING POLICY MUST BE LAST
all		all		REJECT		info
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
```

rules
```
#
#	Accept DNS connections from the fw to the net
#
ACCEPT		fw		net		tcp	53
ACCEPT		fw		net		udp	53
#
#
#	Accept SSH connections from the loc to the fw and vir
#
ACCEPT		loc		fw		tcp	22
ACCEPT		loc		vir		tcp	22
#
#	Make ping work bi-directionally between the net, fw, loc and vir zones
#	(assumes that the loc-> net policy is ACCEPT).
#
ACCEPT		fw		net		icmp
ACCEPT		fw		loc		icmp	
ACCEPT		fw		vir		icmp	
ACCEPT		loc		fw		icmp	8
ACCEPT		loc		vir		icmp	8
ACCEPT		vir		fw		icmp	8
ACCEPT		vir		loc		icmp	8
#ACCEPT		net		fw		icmp	8
#ACCEPT		net		loc		icmp	8	# Only with Proxy ARP and
#ACCEPT		net		vir		icmp	8 	# static NAT
#
#	User define
#
# vnc 5800,5900
ACCEPT		all		fw		tcp	5800,5900
# apache 8000
ACCEPT		all		fw		tcp	8000
# jbidwatcher 9000:9003
ACCEPT		all		fw		tcp	9000:9003
# hlds 27016,27017
ACCEPT		all		fw		tcp	27016,27017
# samba 137:139,445
ACCEPT		fw		loc		udp	137,138
ACCEPT		fw		vir		udp	137,138
ACCEPT		loc		fw		udp	137,138
ACCEPT		loc		vir		udp	137,138
ACCEPT		vir		fw		udp	137,138
ACCEPT		vir		loc		udp	137,138
ACCEPT		fw		loc		tcp	139,445
ACCEPT		fw		vir		tcp	139,445
ACCEPT		loc		fw		tcp	139,445
ACCEPT		loc		vir		tcp	139,445
ACCEPT		vir		fw		tcp	139,445
ACCEPT		vir		loc		tcp	139,445
# emule 2664,2665
DNAT		net		loc:192.168.1.2	tcp	4663
DNAT		net		loc:192.168.1.2	udp	4664
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
```

---

### Post by stanwebber on 2006-04-26
i found the solution:

change IP_FORWARDING=keep to IP_FORWARDING=on in shorewall.conf

---

