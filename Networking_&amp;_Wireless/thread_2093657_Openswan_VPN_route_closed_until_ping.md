---
title: "Openswan VPN route closed until ping"
date: 2012-12-11
forum: Networking &amp; Wireless
---

### Post by Kissell on 2012-12-11
Hey peoples...  I'm trying to setup openswan VPN on a new Ubuntu box, and I got it kinda sorta working.  

The VPN tunnel is up, it's established, and I can ping hosts on both ends of the tunnel...  connectivity is good.  But only after I initiate a connection attempt from the other side.

SIDE A = Juniper VPN
SIDE B = Ubuntu Openswan

SIDE B cannot ping anything on SIDE A's network, until anything on SIDE A pings or otherwise attempts to communicate with something in SIDE B.  Once something in SIDE A tries to connect to something in SIDE B, not only does the connection work, but then it becomes two-way, and anything on SIDE B can now connect to anything on SIDE A.  But before SIDE A attempts a connection, SIDE B cannot communicate with SIDE A.

Weird...  

I've been googling this for awhile and playing with config settings, and just can't resolve this...  anyone have any ideas or had a similar problem in the past?  

ipsec.conf
```
config setup
        virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
        nat_traversal=yes
        protostack=netkey
        oe=no

conn juniper_ssg5_01
	type=tunnel
	authby=secret
	auth=esp
	pfs=no
	rekey=yes
	auto=start
	keylife=1h
	keyingtries=0
	keyexchange=ike
	ike=aes128-md5-modp1024
	phase2alg=aes128-md5

	# Linux Openswan
	leftid=10.1.1.5
	left=10.1.1.5 # expernal ip
	leftsubnet=10.1.0.0/16
	leftsourceip=10.1.1.5

	# Juniper VPN
	rightid=10.254.1.5
	right=66.8.8.8 (not really, my real public IP omitted)
        rightsubnet=10.254.1.0/24

```

---

