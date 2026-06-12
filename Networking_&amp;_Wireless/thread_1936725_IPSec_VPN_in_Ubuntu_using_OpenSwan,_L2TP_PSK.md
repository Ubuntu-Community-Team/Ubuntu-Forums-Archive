---
title: "IPSec VPN in Ubuntu using OpenSwan, L2TP PSK"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by tsubakaran on 2012-03-06
I am trying to setup IPSec VPN using openswan and spent a lot of time by googling, so some can help with your expert.

My router and system as below

---- WAN Link ---Router[192.168.20.1]--- Ubuntu[192.168.20.25]

Version of Linux: Welcome to Ubuntu 11.10 (GNU/Linux 3.0.0-16-server x86_64)

I have done the port forwarding on the router for UDP ports 50, 1701, 500 & 4500

When I try to connect the IPSec VPN with I am getting this error: 

Mar  7 05:32:00 ubuntu pluto[1555]: packet from 92.240.x.x:500: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000008]
Mar  7 05:32:00 ubuntu pluto[1555]: packet from 92.240.x.x:500: received Vendor ID payload [RFC 3947] meth=109, but port floating is off
Mar  7 05:32:00 ubuntu pluto[1555]: packet from 92.240.x.x:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but port floating is off
Mar  7 05:32:00 ubuntu pluto[1555]: packet from 92.240.x.x:500: ignoring Vendor ID payload [FRAGMENTATION]
Mar  7 05:32:00 ubuntu pluto[1555]: packet from 92.240.x.x:500: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Mar  7 05:32:00 ubuntu pluto[1555]: packet from 92.240.x.x:500:  ignoring Vendor ID payload [Vid-Initial-Contact]
Mar  7 05:32:00 ubuntu pluto[1555]: packet from 92.240.x.x:500:  ignoring Vendor ID payload [IKE CGA version 1]
Mar  7 05:32:00 ubuntu pluto[1555]: "L2TP-PSK-NAT"[1] 92.240.x.x   #1: responding to Main Mode from unknown peer 92.240.x.x
Mar  7 05:32:00 ubuntu pluto[1555]: "L2TP-PSK-NAT"[1] 92.240.x.x #1: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Mar  7 05:32:00 ubuntu pluto[1555]: "L2TP-PSK-NAT"[1] 92.240.x.x #1: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Mar  7 05:32:00 ubuntu pluto[1555]: "L2TP-PSK-NAT"[1] 92.240.x.x #1: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Mar  7 05:32:00 ubuntu pluto[1555]: "L2TP-PSK-NAT"[1] 92.240.x.x #1: STATE_MAIN_R1: sent MR1, expecting MI2
Mar  7 05:32:01 ubuntu pluto[1555]: "L2TP-PSK-NAT"[1] 92.240.x.x #1: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Mar  7 05:32:01 ubuntu pluto[1555]: "L2TP-PSK-NAT"[1] 92.240.x.x #1: STATE_MAIN_R2: sent MR2, expecting MI3
Mar  7 05:32:02 ubuntu pluto[1555]: "L2TP-PSK-NAT"[1] 92.240.x.x #1: Main mode peer ID is ID_IPV4_ADDR: '92.240.x.x'
Mar  7 05:32:02 ubuntu pluto[1555]: "L2TP-PSK-NAT"[1] 92.240.x.x #1: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Mar  7 05:32:02 ubuntu pluto[1555]: "L2TP-PSK-NAT"[1] 92.240.x.x #1: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp2048}
Mar  7 05:32:02 ubuntu pluto[1555]: "L2TP-PSK-NAT"[1] 92.240.x.x #1: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Mar  7 05:32:03 ubuntu pluto[1555]: "L2TP-PSK-NAT"[1] 92.240.x.x #1: the peer proposed: 202.175.x.x/32:17/1701 -> 92.240.x.x/32:17/0
Mar  7 05:32:03 ubuntu pluto[1555]: "L2TP-PSK-NAT"[1] 92.240.x.x #1: cannot respond to IPsec SA request because no connection is known for 202.175.x.x/32===192.168.20.25<192.168.20.25>[+S=C]:17/1701...92.240.x.x[+S=C]:17/%any


-------------------------------------------
It is my /etc/ipsec.config file
-------------------------------------------
version	2.0	

config setup
	nat_traversal=no
	virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
	oe=off
	protostack=netkey

conn L2TP-PSK-NAT
    rightsubnet=vhost:%priv
    also=L2TP-PSK-noNAT

conn L2TP-PSK-noNAT
	authby=secret
	pfs=no
	auto=add
	keyingtries=3
	rekey=no
	ikelifetime=8h
	keylife=1h
	type=transport
	left=192.168.20.25
	leftnexthop=192.168.20.1
	leftprotoport=17/1701
	right=%any
	rightprotoport=17/%any
	dpddelay=15
	dpdtimeout=30
	dpdaction=clear


-------------------------------------------
It is my /etc/xl2tpd/xl2pd.conf
-------------------------------------------

[global]
debug network = yes
debug tunnel = yes
ipsec saref = no

[lns default]
ip range = 192.168.20.201-192.168.20.205
local ip = 192.168.20.25
refuse chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
auth file =  /etc/ppp/chap-secrets
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes



-------------------------------------------
It is my /etc/ipsec.secrets
-------------------------------------------

192.168.20.25   %any: PSK "ADbc125634"




-------------------------------------------
it is my /etc/ppp/chat-secrets
-------------------------------------------

# client        server          secret          IP addresses
testuser        ubuntu          p@ssw0rd        *



-------------------------------------------
It is my /etc/ppp/options.xl2tpd
-------------------------------------------

require-mschap-v2
ms-dns 192.168.20.1
asyncmap 0
auth
crtscts
lock
hide-password
modem
debug
name l2tpd
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4

-------------------------------------------

I rebooted and started ipsec. It produced the log under the /var/log/auth.log
root@ubuntu:~# /etc/init.d/ipsec start
ipsec_setup: Stopping Openswan IPsec...
ipsec_setup: Starting Openswan IPsec U2.6.28/K3.0.0-16-server...

root@ubuntu:~# tail -f /var/log/auth.log
Mar  7 05:29:54 ubuntu pluto[1555]: Changed path to directory '/etc/ipsec.d/ocspcerts'
Mar  7 05:29:54 ubuntu pluto[1555]: Changing to directory '/etc/ipsec.d/crls'
Mar  7 05:29:54 ubuntu pluto[1555]:   Warning: empty directory
Mar  7 05:29:54 ubuntu pluto[1555]: added connection description "L2TP-PSK-NAT"
Mar  7 05:29:54 ubuntu pluto[1555]: added connection description "L2TP-PSK-noNAT"
Mar  7 05:29:54 ubuntu pluto[1555]: listening for IKE messages
Mar  7 05:29:54 ubuntu pluto[1555]: adding interface eth0/eth0 192.168.20.25:500
Mar  7 05:29:54 ubuntu pluto[1555]: adding interface lo/lo 127.0.0.1:500
Mar  7 05:29:54 ubuntu pluto[1555]: adding interface lo/lo ::1:500
Mar  7 05:29:54 ubuntu pluto[1555]: loading secrets from "/etc/ipsec.secrets"

then tried, same error as above. Can anybody help me.

---

