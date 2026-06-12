---
title: "DHCP fails to service subnet"
date: 2012-12-08
forum: Networking &amp; Wireless
---

### Post by enesman on 2012-12-08
Trying to use isc-dhcp-server to furnish IP address to an HDHomerun Prime connected to eth1 of my HTPC. The following appears in my syslog:

```
Dec  8 14:25:21 dvr kernel: [    5.486114] init: isc-dhcp-server main process ended, respawning
Dec  8 14:25:21 dvr dhcpd: Internet Systems Consortium DHCP Server 4.1-ESV-R4
Dec  8 14:25:21 dvr dhcpd: Copyright 2004-2011 Internet Systems Consortium.
Dec  8 14:25:21 dvr dhcpd: All rights reserved.
Dec  8 14:25:21 dvr dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Dec  8 14:25:21 dvr dhcpd: Internet Systems Consortium DHCP Server 4.1-ESV-R4
Dec  8 14:25:21 dvr dhcpd: Copyright 2004-2011 Internet Systems Consortium.
Dec  8 14:25:21 dvr dhcpd: All rights reserved.
Dec  8 14:25:21 dvr dhcpd: For info, please visit https://www.isc.org/software/dhcp/
Dec  8 14:25:21 dvr dhcpd: Wrote 0 deleted host decls to leases file.
Dec  8 14:25:21 dvr dhcpd: Wrote 0 new dynamic host decls to leases file.
Dec  8 14:25:21 dvr dhcpd: Wrote 0 leases to leases file.
Dec  8 14:25:21 dvr dhcpd: 
Dec  8 14:25:21 dvr dhcpd: No subnet declaration for eth1 (no IPv4 addresses).
Dec  8 14:25:21 dvr dhcpd: ** Ignoring requests on eth1.  If this is not what
Dec  8 14:25:21 dvr dhcpd:    you want, please write a subnet declaration
Dec  8 14:25:21 dvr dhcpd:    in your dhcpd.conf file for the network segment
Dec  8 14:25:21 dvr dhcpd:    to which interface eth1 is attached. **
Dec  8 14:25:21 dvr dhcpd: 
Dec  8 14:25:21 dvr dhcpd: 
Dec  8 14:25:21 dvr dhcpd: Not configured to listen on any interfaces!
Dec  8 14:25:21 dvr kernel: [    5.506687] init: isc-dhcp-server main process (1537) terminated with status 1
Dec  8 14:25:21 dvr kernel: [    5.506712] init: isc-dhcp-server respawning too fast, stopped

```
Evidently service requests are appearing at eth1 but the dhcp-server is not able to see dhcpd.conf file defining the subnet.

I have set up the following three files:-

/etc/network/interfaces

```
auto lo
iface lo inet loopback

iface eth1 inet static
    address 169.254.0.1
    netmask 255.255.0.0

```

/etc/default/isc-dhcp-server

```
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/isc-dhcp-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"
```

/etc/dhcp/dhcpd.conf (partial shown; remainder commented out.

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
# authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

subnet 169.254.0.0 netmask 255.255.0.0 {
}

host 1314400A {
  hardware ethernet 00:18:DD:31:44:00;
  fixed-address 169.254.0.2;
}


```

System software is Mythbuntu 12.04.1.

Any suggestions for tracking down source of problem?

SOLVED:

Removed "remark" symbol (#) from "authoritative" line in file /etc/dhcp/dhcpd.conf.

---

