---
title: "DHCP3 reservations being ignored?"
date: 2011-03-30
forum: Networking &amp; Wireless
---

### Post by yeleek on 2011-03-30
Hi,

Have DHCP3 running on an ubuntu server.  Using config of the below but the 10.1.1.2 address is being given to a windows pc (which does not have that MAC address).  Tried getting windows to release ip address, then clearing the lease file and restarting dhcp3 service, then renewing dhcp request from windows, but address 10.1.1.2 is still given.  ANy ideas please?

```
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
option domain-name "home.local";
option domain-name-servers ns.home.local;

default-lease-time 21600;
max-lease-time 86400;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

#  Configuration for 10.1.1.0/24 subnet.
subnet 10.1.1.0 netmask 255.255.255.0 {
range 10.1.1.2 10.1.1.20;
option domain-name-servers ns.home.local;
option domain-name "ns.home.local";
option routers 10.1.1.1;
option broadcast-address 10.1.1.255;
default-lease-time 21600;
max-lease-time 86400;
}
# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

host wopr {
hardware ethernet 6C:F0:49:02:3F:D9;
fixed-address 10.1.1.2;
}


```

---

### Post by yeleek on 2011-03-30
OK I'm a fool.  I thought I could reserve addresses within the range.  What has now worked is changing the range to 10.1.1.5 but keeping 10.1.1.2 for wopr.

Sure enough windows pc is using 10.1.1.5 and wopr is using 10.1.1.2

Resolved.

---

