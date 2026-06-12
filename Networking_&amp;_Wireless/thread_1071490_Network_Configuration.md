---
title: "Network Configuration"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by Gaurang02 on 2009-02-16
Hi i have attached the LAN cable to my pc and the net is working very well

now i want to setup the network for sharing data to other pc.

so i wrote in interfaces file

interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 10.0.0.77
	netmask 255.255.255.0
	gateway 192.168.1.1
	broadcast 192.168.1.77

	
and i wrote in Hosts file

192.168.1.77 	localhost server.localhost
10.0.0.77	prosesindia.local.lan

# The following lines are desirable for Ipv6 capable hosts

::1 	localhost ip6-localhost
       	          ip6-loopback

fe00 :: 0 ip6-localnet
ff00 :: 0 ip6-mcastprefix
ff02 :: 1 ip6-allnodes
ff02 :: 2 ip6-allrouters
ff02 :: 3 ip6-allhosts

and  i wrote in the resolv.conf file

my domain local.lan
search local.lan
192.168.1.1


after that when i restart networking via sudo /etc/init.d/networking restart

it gives me error
eth1 : ERROR while getting interface flags: no such device


how to remove this error and do network setup?

waiting for reply

Thanks
Regards
Gaurang

---

