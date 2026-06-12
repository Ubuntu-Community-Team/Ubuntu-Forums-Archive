---
title: "cant install dhcp for firestarter"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by willow370 on 2012-01-02
hi all, what i thought was a simple instruction for setting up firestarter has become more difficult than i thought.

ive read instructions on installing dhcp for firestarter and it says to run this command in terminal to install the dhcp software

sudo apt-get install dhcp

and it tells me that theres no software called this, but may be called something else, but ive read a few of these tutorials on the internet and they all say to use the command above.

any ideas?

what i ultimately want is to enable dhcp when setting up firestarter (via the wizard)

im running ubuntu 11.10

cheers

---

### Post by spiky001 on 2012-01-02
Firestarter is well out of date and not maintained any more

---

### Post by willow370 on 2012-01-02
is there similar software out there or another peice of dhcp software thats compatible with firestarter?

---

### Post by collisionystm on 2012-01-02
> **willow370 said:**
> hi all, what i thought was a simple instruction for setting up firestarter has become more difficult than i thought.

ive read instructions on installing dhcp for firestarter and it says to run this command in terminal to install the dhcp software

sudo apt-get install dhcp

and it tells me that theres no software called this, but may be called something else, but ive read a few of these tutorials on the internet and they all say to use the command above.

any ideas?

what i ultimately want is to enable dhcp when setting up firestarter (via the wizard)

im running ubuntu 11.10

cheers


are you trying to do internet sharing?

---

### Post by willow370 on 2012-01-02
yep trying to

on a side note, i think it may be because theres no dhcp server configured. so im trying to configure one via this help tutorial

[https://help.ubuntu.com/11.10/serverguide/C/dhcp.html](https://help.ubuntu.com/11.10/serverguide/C/dhcp.html)

it says, edit /etc/dhcp/dhcpd.conf and change to the following info

```
# minimal sample /etc/dhcp/dhcpd.conf default-lease-time 600; max-lease-time 7200;  subnet 192.168.1.0 netmask 255.255.255.0 {  range 192.168.1.150 192.168.1.200;  option routers 192.168.1.254;  option domain-name-servers 192.168.1.1, 192.168.1.2;  option domain-name "mydomain.example"; } 
```

but inside my /etc/dhcp/dhcpd.conf is this

```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
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

its nothing like it :S

---

### Post by willow370 on 2012-01-02
so i decided to take a slightly different aproach and tried this way

[http://www.basicconfig.com/linuxnetwork/configure_dhcp_server_ubuntu](http://www.basicconfig.com/linuxnetwork/configure_dhcp_server_ubuntu)

but its all revolved around the file /etc/dhcp3/dhcpd.conf which doesnt exist even though ive installed dhcp3 (i know this because i have /etc/dhcp3... but no file inside, just another folder labeled "dhclient-enter-hooks.d" with a samba file inside.

is dhcp3 out of date or something? is it not configured for 11.10?

---

### Post by willow370 on 2012-01-02
ok through much playing around ive managed to create the file in the folder and add the sample code given, but how do i know what ip addresses and subnet masks to use?

---

