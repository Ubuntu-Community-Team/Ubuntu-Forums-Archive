---
title: "Ubuntu server 10.10 IPSEC No KLIPS support?"
date: 2010-11-26
forum: Networking &amp; Wireless
---

### Post by remoteitservices on 2010-11-26
Hi,
 
Whe are trying to get ipsec to work on our ubuntuserver 10.10
 
When starting ipsec it says :
 
ipsec_setup: Starting Openswan IPsec 2.6.26...
ipsec_setup: No KLIPS support found while requested, desperately falling back to netkey
ipsec_setup: NETKEY support found. Use protostack=netkey in /etc/ipsec.conf to avoid attempts to use KLIPS. Attempting to continue with NETKEY
 
Whe need KLIPS because the hardware firewall on the other side is using KLIPS
 
The command ipsec verify gives :
 
# ipsec verify 
/usr/local/sbin/ipsec: unknown IPsec command `verify' (`ipsec --help' for list)
 
My ipsec.conf
 
config setup
# plutodebug / klipsdebug = "all", "none" or a combation from below:
# "raw crypt parsing emitting control klips pfkey natt x509 private"
# eg:
# plutodebug="control parsing"
#
# Only enable klipsdebug=all if you are a developer
#
# NAT-TRAVERSAL support, see README.NAT-Traversal
nat_traversal=no
# virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
#
# enable this if you see "failed to find any available worker"
nhelpers=0
#interfaces="ipsec0=eth1"
#Disable Opportunistic Encryption
include /etc/ipsec.d/examples/no_oe.conf
# Add connections here
# sample VPN connections, see /etc/ipsec.d/examples/
include /etc/ipsec.d/configs/ipsec.customer.conf
 
And my ipsec.customer.conf:
 
## Gateway-to-gateway: Customer <-> Ourselves
conn type=tunnel
# Left side is Customer
left=**.169.154.2
# leftnexthop=
leftsubnet=**.31.0.0/22
# Right side is Ourselves
right=**.161.152.77
# rightnexthop=
# rightsubnet=**.161.152.77/32
keyexchange=ike
ikelifetime=8h
keylife=1h
auth=esp
auto=start
authby=secret
 
And a piece of my syslog:
 
Nov 26 11:31:10 gw002 ipsec_setup: Using KLIPS/legacy stack
Nov 26 11:31:11 gw002 ipsec_setup: No KLIPS support found while requested, desperately falling back to netkey
Nov 26 11:31:11 gw002 ipsec_setup: NETKEY support found. Use protostack=netkey in /etc/ipsec.conf to avoid attempts to use KLIPS. Attempting to continue with NETKEY
Nov 26 11:31:11 gw002 ipsec_setup: Using NETKEY(XFRM) stack
Nov 26 11:31:11 gw002 ipsec_setup: ...Openswan IPsec started
Nov 26 11:31:11 gw002 ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d
Nov 26 11:31:11 gw002 pluto: adjusting ipsec.d to /etc/ipsec.d
Nov 26 11:31:11 gw002 ipsec__plutorun: 002 added connection description "customer-ourselves"
Nov 26 11:31:11 gw002 ipsec__plutorun: 104 "customer-ourselves" #1: STATE_MAIN_I1: initiate
 
Hope somebody can help me out on this.

---

### Post by slinkygn on 2011-03-08
Did you get this one figured out?

---

### Post by fabioa1978 on 2011-05-05
Hello All,

I have almost the same issue. I cant figure it out! i have OPENSWAN installed and ipsec.conf configured, but when I try to excute, I have the same problems with the following errors.
The OPENVPN it starts perfectly, can you help!!!

Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                 [OK]
Linux Openswan U2.6.28/K2.6.38-8-generic-pae (netkey)
Checking for IPsec support in kernel                            [OK]
NETKEY detected, testing for disabled ICMP send_redirects       [FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/send_redirects
  or NETKEY will cause the sending of bogus ICMP redirects!

NETKEY detected, testing for disabled ICMP accept_redirects     [FAILED]

  Please disable /proc/sys/net/ipv4/conf/*/accept_redirects
  or NETKEY will accept bogus ICMP redirects!

Checking that pluto is running                                  [OK]
Pluto listening for IKE on udp 500


I dont know what to do anymore,  Can you guys help me with this??

Checking NAT and MASQUERADEing
Checking for 'ip' command                                       [OK]
Checking for 'iptables' command                                 [OK]


Thanks

---

### Post by wlraider70 on 2011-05-11
I've woked on this a bit I dont have all the answers, but if you want to change those values to deny redirects

```

sudo -i
echo 0 > /proc/sys/net/ipv4/conf/**all**/send_redirects
exit 

```

There are several "redirect" files in several folders 
All
default
eth
(something else)

Changing the value in them to 0 means, no do not redirect.


**definitely no warranty here*

---edit
just came across this


As root, you can just write 0 into each of those files.

For persistence across reboots you can you can put these settings in /etc/sysctl.conf

Running

sudo sysctl -a | grep 'ipv4.conf.*redirect'

should list the variables you need to set. (Note: set them all to 0).

Running sudo sysctl -p will process it.

---

