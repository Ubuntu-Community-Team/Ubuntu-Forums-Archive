---
title: "Home Networking, 2 NICs 1 ADSL modem &amp; 1 Wireless Router &amp; ubuntu 9.04"
date: 2009-07-28
forum: Networking &amp; Wireless
---

### Post by ZOOSERVE on 2009-07-28
I have worked with Centos Web servers for about 2 years, but am new to Home Networking, Routing & ubuntu.

I am trying to set up a Home Network with the below Configuration

I have Ubuntu 9 Desktop with most all server components Installed on my Ubuntu Box

I have 2 NICs with a D-Link 500G ADSL modem hooked up to 1 NIC eth0, 
and a D-Link DI-524 Wireless Router hooked up to the second NIC eth1, 
and then have several workstations with Wireless Cards thoughout the House.

I have DHCP enabled on both the modem and router and of course on the server have a good NAT enabled Internet Connection via PPOE 

However I cant seem to enable the NIC for the Wireless Router
Some one mentioned it had to do with /etc/network/interfaces

-------------------------------------------------------------------------------------------------------
$ nano /etc/network/interfaces

auto lo
iface lo inet loopback
-------------------------------------------------------------------------------------------------------

is what i have in /etc/network/interfaces

I must admit when it comes to routing I am lost
Perhaps if someone could point me in the right direction with this set up
I have attached a gif of my network layout but am not sure where to begin as far as

1. getting the second NIC to work for the router 
2. Routing Manualy from the ADSL modem to the server and from the server to the router (setting up IPs subnetmasks etc)

Thanks for any advice

---

### Post by superprash2003 on 2009-07-28
i presume the basic idea is internet connection sharing? if so , follow this tutorial [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) ..and disable DHCP server in your wifi router as it should not be considered as the gateway.. you could either use static ip or seutp a dhcp server in ubuntu

---

### Post by Bucky Ball on 2009-07-28
Yes, wireless access point only.

I have a wired D-Link 704P and a D-Link wireless same as yours from memory. Modem is plugged into WAN port of 704P (192.168.0.1), Wireless router connected *via a LAN port* with an ethernet cable to the 704P and set to 192.168.0.2 and AP only. The 'P' in the 704P stands for print server which is why everything comes and goes from there. 

DHCP off on all machines and routers (and in the D-Links, you need to disable static as well as DHCP server) and *static set on the Ubuntu machines* using the System->Admin->Network GUI. It makes life and networking in Ubuntu a whole lot easier. I learnt this after months on and off of trying to set it up!

192.168.0.1 (the 704P wired router)
255.255.255.0
Your Static IP HERE. 

Gateway, naturally, the *wired* 704P. The above Network setting applies to your wireless devices also! They should *not* be set to 192.168.0.2 (the wireless router) but the wired one.

Not exactly what you're doing but hope it is of some help. Thought I'd throw it in as I'm familiar with the D-Links (and a bit of a fan, actually). Good luck with it. :)

---

### Post by ZOOSERVE on 2009-07-28
Thanks for the suggestions
but I believe this is more what i am looking for [http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html) to use dhcp client for eth0 for the server to connect to the ADSL modem which I have working



```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:2f:ed:3f:41
Sending on   LPF/eth0/00:11:2f:ed:3f:41
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 10.1.1.1 port 67
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:11:2f:ed:3f:41
Sending on   LPF/eth0/00:11:2f:ed:3f:41
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 10.1.1.4 from 10.1.1.1
DHCPREQUEST of 10.1.1.4 on eth0 to 255.255.255.255 port 67
DHCPACK of 10.1.1.4 from 10.1.1.1
bound to 10.1.1.4 -- renewal in 118858 seconds.
```and DHCP Server to connect to the wireless router on eth1 but following the directions above I keep getting the error on dhcp server restart
```
No subnet declaration for eth1:avahi (0.0.0.0).
```

---

### Post by superprash2003 on 2009-07-29
post your dhcpd.conf file here

---

### Post by ZOOSERVE on 2009-07-29
dhcp.conf as follows

```
test@ubuntu-server:/etc/dhcp3$ cat dhcpd.conf
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

```

---

### Post by superprash2003 on 2009-07-30
hmm.. most of that file is commented out.. check out this dhcpd.conf file and try tweaking it [http://www.prash-babu.com/2009/05/how-to-enable-dhcp-server-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-enable-dhcp-server-in-ubuntu.html)

---

### Post by ZOOSERVE on 2009-07-30
sorry i posted the wrong one as i went back to the original

I had tried that as was suggested in the thread i posted earlier

i keep getting a syntax error at [B]option domain-name “mydomain”;

says it requires a semi colon but obviously there is a semi colon

thanks
[/B]

---

