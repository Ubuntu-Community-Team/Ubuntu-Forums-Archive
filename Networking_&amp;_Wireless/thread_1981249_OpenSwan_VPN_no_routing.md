---
title: "OpenSwan VPN no routing"
date: 2012-05-16
forum: Networking &amp; Wireless
---

### Post by wilfred_com on 2012-05-16
Hello friends

I'm configuring a site-to-site VPN for a client but have problems with the routes, my tunnel is up and everything seems to be ok, but i have no communication between my two networks.
One point is a Precise Ubuntu Box and the other a CISCO ASA 5540

If the openswan service is down and i try to do a "traceroute" against the subnet i'm trying to connect the package is send trough the default route an jump until didn't find the route, this is obviously a normal behaviour:

$ traceroute 192.168.202.22
traceroute to 192.168.202.22 (192.168.202.22), 30 hops max, 60 byte packets
 1  * * *
 2  172.31.250.46 (172.31.250.46)  14.903 ms  14.916 ms  16.554 ms
 3  190.157.7.149 (190.157.7.149)  17.566 ms  17.568 ms  17.570 ms
 4  10.14.14.126 (10.14.14.126)  79.087 ms  79.102 ms  79.106 ms
 5  64.86.28.41 (64.86.28.41)  73.006 ms !H * *

But if the service is up and the tunnel established, the package doesn't route:
$ traceroute 192.168.202.22
traceroute to 192.168.202.22 (192.168.202.22), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * * *

The routing table BEFORE the tunnel is:

 $ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         190.147.229.10   0.0.0.0         UG    100    0        0 eth0
190.147.229.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.5.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2

And AFTER the tunnel is:
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         190.147.229.10   0.0.0.0         UG    100    0        0 eth0
190.147.229.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.5.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
192.168.202.0   0.0.0.0         255.255.255.0   U     0      0        0 ipsec0


This are my configuration fiel ipsec.conf:
config setup
    # Do not set debug options to debug configuration issues!
    # plutodebug / klipsdebug = "all", "none" or a combation from below:
    # "raw crypt parsing emitting control klips pfkey natt x509 dpd private"
    # eg:
    plutodebug=none
    klipsdebug=none

    #
    # enable to get logs per-peer
    plutoopts="--perpeerlog"
    #
    # Again: only enable plutodebug or klipsdebug when asked by a developer
    #
    # NAT-TRAVERSAL support, see README.NAT-Traversal
    nat_traversal=yes
    # exclude networks used on server side by adding %v4:!a.b.c.0/24
    #virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
    #interfaces="ipsec0=eth0"

    # OE is now off by default. Uncomment and change to on, to enable.
    #oe = off
    # which IPsec stack to use. netkey,klips,mast,auto or none
    protostack=klips
    #nhelpers = 0
    plutostderrlog=/var/log/vpn

# Add connections here
conn net-super
    type=tunnel
    authby=secret                # Key exchange method
    left=190.147.229.35          # Public Internet IP address of the
    leftsubnet=192.168.0.0/24     # Subnet protected by the LEFT VPN device
    leftnexthop=190.147.229.10     # correct in many situations
    right=190.26.206.148         # Public Internet IP address of
    rightsubnet=192.168.202.0/24      # Subnet protected by the RIGHT VPN device
    rightnexthop=%defaultroute
    auto=start                   # authorizes and starts this connection
    aggrmode=no
    keyexchange=ike
    ike=3des-sha1-modp1024
    phase2=esp
    phase2alg=3des-sha1
    pfs=no

Even the firewall is with all default policies opened (ACCEPT) i set a few rules to allow the traffic:
Table Nat:
-A POSTROUTING -m policy -d 192.168.202.0/24 -o eth0 -j ACCEPT  --dir out --pol ipsec
Table Filter:
-A INPUT -m policy -j ACCEPT  --dir in --pol ipsec
-A INPUT -p esp -j ACCEPT
-A INPUT -p udp -m udp -m multiport -j ACCEPT --dports 500,4500
-A FORWARD -m policy -j ACCEPT  --dir in --pol ipsec

The last log (and output of ipsec auto --status) entries are:
000 #2: "net-super":500 STATE_QUICK_I2 (sent QI2, IPsec SA established); EVENT_SA_REPLACE in 27194s; newest IPSEC; eroute owner; isakmp#1; idle; import:admin initiate
000 #2: "net-super" esp.db0b6ee1@190.26.206.148 esp.7f45d825@190.147.229.35 tun.1001@190.26.206.148 tun.1002@190.147.229.35 ref=3 refhim=1
000 #1: "net-super":500 STATE_MAIN_I4 (ISAKMP SA established); EVENT_SA_REPLACE in 1828s; newest ISAKMP; lastdpd=4s(seq in:0 out:0); idle; import:admin initiate

And the ipsec route shows:
$ipsec eroute
0          192.168.0.0/24     -> 192.168.202.0/24   => tun0x1001@190.26.206.148


In theory all is right but the server and the subnet 192.168.0.0/24 can't contact the subnet 192.168.202.0/24.


Please any help is welcomed, i googled and made many different variations of the config but without result.

---

