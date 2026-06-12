---
title: "DHCP server with IP routing between NICs"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by BarryDocks on 2009-11-14
Wonder if anyone can help me, I have spent along time not really getting very far!

Currently, this is the setup where the Fileserver is connected to the DHCP router via network interface ETH0 and is a DCHP-client (IP address range 192.168.1.1 to 192.168.1.10).  Fileserver network interface ETH2 is a DHCP server for a separate network of clients with exclusive IP addresses (135.120.135.1 to 135.120.135.10) via a gigabit switch.  
     
Problem:  is that I a currently unable to access the WAN from the clients on ETH2.

I think I need some sort of IP routing or gateway routing?

/etc/dhcp3/dhcpd.conf is:
```
##########################################################
#
# DHCP CLIENT CONFIGURATION SETTINGS
#

# use ad-hoc style name server updating procedures
ddns-update-style ad-hoc; 

# this may be required for some network configurations,
# but seems to work fine without it on my LAN.
#option domain-name "my-dhcp-server.com";

#assign the remote dhcp server hostname/ip addresses 
option domain-name-servers 192.168.4.100, 192.168.8.100;

##########################################################
#
# DHCP SERVER CONFIGURATION SETTINGS 
#

# assign the defaul lease time (seconds)
default-lease-time 600000000;

# assign the max lease time (seconds)
max-lease-time 720000000;

# eth2 subnet configuration
subnet 135.120.135.0 netmask 255.255.255.0 {
	authoritative;
	allow client-updates;
	allow unknown-clients;
	range 135.120.135.1 135.120.135.10;
# assigns default gateway	
	option routers 135.120.135.1;
	option broadcast-address 135.120.135.255;
	}

# eth1 subnet configuration
#subnet 192.168.2.0 netmask 255.255.255.0 {
#  range 192.168.2.2 192.168.2.99;
#  option routers 192.168.2.1;
#  option broadcast-address 192.168.2.255;
#}

##########################################################
# end config
```

/etc/network/interface is:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth2 inet static
	address 135.120.135.1
	netmask 255.255.255.0
	broadcast 135.120.135.255
	gateway 135.120.135.1

```

I'd be grateful for some help

---

### Post by Iowan on 2009-11-14
[This]("https://help.ubuntu.com/community/Internet/ConnectionSharing") ICS help page may provide the information you need.

---

