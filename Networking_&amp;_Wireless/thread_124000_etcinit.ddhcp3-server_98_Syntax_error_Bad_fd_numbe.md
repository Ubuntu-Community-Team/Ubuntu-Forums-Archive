---
title: "/etc/init.d/dhcp3-server: 98: Syntax error: Bad fd number"
date: 2006-01-31
forum: Networking &amp; Wireless
---

### Post by AcidTripp on 2006-01-31
I'm trying to set up a local network, which shares a wireless connection (I don't have access to the wireless router).
I'm trying to set up my main PC as a gateway between the wireless connection (ra0), and the local subnet (eth0), hooked up to a hub.

I followed the [Ubuntu Router Guide]("http://ubuntuforums.org/showthread.php?t=119787&highlight=dhcpd"), but every time I try:
```
sudo /etc/init.d/dhcp3-server start
```
I get the error:
```
/etc/init.d/dhcp3-server: 98: Syntax error: Bad fd number
```

Here's my /etc/dhcp3/dhcpd.conf:
```
##########################################################
#
# Configuration Notes:
#
# This configuration file assumes that you
# have a total of 4 NIC cards installed on your system,
# with eth2 connecting (as a client) to a remote dhcp server.
#
# This will assign a dhcp subnet to each additional NIC card
# (eth1, eth0), which can be used to create a
# multi-subnet DHCP Server.
#
# Example by: Sean O'Donnell http://code.seanodonnell.com
#
##########################################################
#
# DHCP CLIENT CONFIGURATION SETTINGS
#

# use ad-hoc style name server updating procedures
ddns-update-style ad-hoc;

# this may be required for some network configurations,
# but seems to work fine without it on my LAN.
option domain-name "router.com";

#assign the remote dhcp server hostname/ip addresses
option domain-name-servers 69.145.232.32, 69.144.49.29, 69.145.232.4;

##########################################################
#
# DHCP SERVER CONFIGURATION SETTINGS
#

# assign the defaul lease time (seconds)
default-lease-time 600000000;

# assign the max lease time (seconds)
max-lease-time 720000000;

# eth0 subnet configuration
subnet 192.168.2.0 netmask 255.255.255.0 {
  range 192.168.2.2 192.168.2.99;
  option routers 192.168.2.1;
  option broadcast-address 192.168.2.255;
}


##########################################################
# end config
```

And my /etc/default/dhcp3-server:
```
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#       Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"
```

I've tracked the problem down to test_config in the /etc/init.d/dhcp3-server.
It seems that the configuration file is somehow poorly formatted, but other than some very minor modifications I just copied and pasted from the Ubuntu Router Guide... any ideas?

---

### Post by AcidTripp on 2006-02-01
Fixed it.
Turns out LOTS of programs have issues when dash is installed as /bin/sh.
dhcp3-server turns out to be one of them

---

