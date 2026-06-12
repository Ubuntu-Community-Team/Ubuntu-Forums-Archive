---
title: "Automatic update of DNS server for static addresses"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by babis85 on 2009-03-20
Hello, i have a problem that can't find its solution. I hava a laptop that i use it at several places with wireless access and at work with wired static address. What i want is whenever i move from one place to another have the laptop be connected automatically without a single keystroke and without using the Network Manager at all. I have succeeded in that, but there are two annoying subproblems.

1. When i move to work the nameserver is not updated automatically in /etc/resolv.conf, so i have to manually edit it and put the respective nameserver.

2. When i am at a place with wireless access eth1 interface is assigned correctly the ip via dhcp, but eth0 interface is up too and i have to bring it down first in order to route through eth1.

Below, i give you my /etc/network/interfaces file:

```
auto lo eth1 eth0
iface lo inet loopback

mapping eth1
	script guessnet-ifupdown
	# Disable open net checking, just comment out if you are
	# desperate enough :) (see relative stanza below)
	map !eth1-anyopen
	# Scan only logical interfaces named eth1-*
	# autofilter: true


iface eth1-profile1 inet dhcp
	pre-up /etc/init.d/iptables start
	wireless-essid profile1
	wireless-key key1
	# Match a wireless network with the given essid
	# If you have spaces in the essid, use double quotes
	test wireless essid profile1
	post-down /etc/init.d/iptables stop


iface eth1-profile2 inet dhcp
	pre-up /etc/init.d/iptables start
	wireless-essid profile2
	wireless-key key2
	# Match a wireless network with the given essid
	# If you have spaces in the essid, use double quotes
	test wireless essid profile2
	post-down /etc/init.d/iptables stop


iface eth1-anyopen inet dhcp
	pre-up /etc/init.d/iptables start
	# You can also match any open network, if you are desperate :)
	wireless-essid any
	wireless-mode auto
	test wireless open
	post-down /etc/init.d/iptables stop

iface eth0 inet static
	pre-up /etc/init.d/iptables start
	address 19x.13x.6x.109
	netmask 255.255.255.0
	network 19x.13x.6x.0
	gateway 19x.13x.6x.1
	# dns-nameservers 19x.13x.yyy.90 (this option is obsolete and does not work at all)
	# test missing-cable
	post-down /etc/init.d/iptables stop

```

Thanks a lot for your help.

---

