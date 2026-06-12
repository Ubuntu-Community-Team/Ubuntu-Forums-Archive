---
title: "Setting up VLAN with Squid and DHCP"
date: 2012-09-04
forum: Networking &amp; Wireless
---

### Post by Zebisnz on 2012-09-04
Hi,

I am trying to add a VLAN to a working transparent proxy, and just need a few pointers as to what I am doing wrong.
I have added VLAN 20 to interfaces with an IP of 192.168.2.1
I don't really understand squid/iptables all that well but have given it a shot as per below. I don't appear to see any DHCP response on VLAN 20, or see the server/proxy itself. The 10.x.x.x network works fine.

 /etc/network/interfaces
```
	iface lo inet loopback
	# External Interface
	auto eth0
	iface eth0 inet static
	address 192.168.1.10
	network 192.168.1.0
	netmask 255.255.255.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
	dns-nameservers x.x.x.x x.x.x.x

	post-up iptables-restore < /etc/iptables.up.rules

	#Internal Interface
	auto eth1
	iface eth1 inet static
	address 10.1.1.250
	network 10.0.0.0
	netmask 255.0.0.0
	broadcast 10.255.255.255

	#VLAN Interface I want to use
	auto eth1.20
	iface eth1.20 inet static
	address 192.168.2.1
	network 192.168.2.0
	netmask 255.255.255.0
	broadcast 192.168.2.255
```

 /etc/dhcp/dhcpd.conf
```
	INTERFACES="eth1.20"
	ddns-update-style none;
	default-lease-time 600;
	max-lease-time 7200;
	log-facility local7;

	subnet 192.168.2.0 netmask 255.255.255.0 {
        option routers 192.168.2.1;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.2.255;
        option domain-name-servers x.x.x.x, x.x.x.x;
        range 192.168.2.11 192.168.2.254;
        }
```

 /etc/squid3/squid.conf (truncated)
```
	acl InternalLAN src 10.0.0.0/8 192.168.2.0/24
	http_access allow InternalLAN
```

 /etc/iptables.up.rules (I am only guessing what to do here)
```
	*nat
	-A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 10.1.1.250:3128
	-A PREROUTING -i eth1.20 -s 192.168.2.0/24  -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.2.1:3128

	-A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
	-A PREROUTING -i eth1.20 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128

	-A POSTROUTING -s 10.0.0.0/8 -o eth0 -j MASQUERADE
	-A POSTROUTING -s 192.168.2.0/24 -o eth0 -j MASQUERADE
	COMMIT
```

---

