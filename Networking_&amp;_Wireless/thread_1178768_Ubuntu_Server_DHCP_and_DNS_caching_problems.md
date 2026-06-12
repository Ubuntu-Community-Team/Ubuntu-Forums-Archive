---
title: "Ubuntu Server DHCP and DNS caching problems"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by mcgodx on 2009-06-04
Hey all,

I recently built a small home server on an Atom box and I was intending it to be a Samba server as well as handling DHCP requests and DNS.

The problem I am running in to seems to be that the hosts are keeping their old IP addresses (the Linksys router I have used to hand out 192.168.1.100-254 for IP addresses).  I assigned my server the static address 192.168.1.100, which I suppose I can easily change however the bigger thing is that it seems to not be handing out IPs because even after I release and renew the addresses, they get the same exact one as before (I know something is wrong because the range I told the server to hand out is 192.168.1.2-10).

I'm not sure what I could be doing wrong so I will post the contents of the config files:

```
mylan@server:~$ cat /etc/dhcp3/dhcpd.conf 
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
#option domain-name "example.org";
#option domain-name-servers ns1.example.org, ns2.example.org;

#default-lease-time 600;
#max-lease-time 7200;

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
subnet 192.168.1.0 netmask 255.255.255.0 {
  range 192.168.1.2 192.168.1.99;
  option domain-name-servers 192.168.1.100;
  option domain-name "internal.example.org";
  option routers 192.168.1.1;
  option broadcast-address 192.168.1.255;
  default-lease-time 600;
  max-lease-time 7200;
}

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

```
mylan@server:~$ cat /etc/default/dhcp3-server 
# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"

```

I'm really at a loss as to what's going on, could my Linksys router be intercepting the DHCP requests?  I kinda need it for wireless, otherwise I'd toss it (no gigabit).  I can access the server using SSH and I can also access the Samba shares just fine with no problem.  DNS caching also seems to work (judging by dig response times).

Thanks any help would be greatly appreciated!

---

### Post by Iowan on 2009-06-04
Your range is 192.168.1.2 - 192.168.1.99 (not 2-10), but that shouldn't affect operation.  Did you restart DHCP after configuring? (**/etc/init.d/dhcp3-server restart**)  I also noticed (for the first time) this line:> # Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.Does that file exist?

BTW, have you tried temporarily disconnecting the router? (If you decide to toss it, I can provide a box... maybe even postage ;) )

---

### Post by mcgodx on 2009-06-04
> **Iowan said:**
> Your range is 192.168.1.2 - 192.168.1.99 (not 2-10), but that shouldn't affect operation.  Did you restart DHCP after configuring? (**/etc/init.d/dhcp3-server restart**)  I also noticed (for the first time) this line:Does that file exist?

BTW, have you tried temporarily disconnecting the router? (If you decide to toss it, I can provide a box... maybe even postage ;) )

Haha thanks for the reply, I appreciate it but I tried all those steps.  Yeah I noticed that too.  For now I have turned off the DHCP service on the server because it was giving me some hassle, however that file does not exist.  I don't have a crossover cable handy (this is a home environment not a business/corporate one) so I can't test DHCP bypassing the router.

The more I think about it, I am thinking somehow the Linksys router is stopping DHCP requests although it doesn't make much sense.

---

### Post by Iowan on 2009-06-04
The machine will respond to whichever DHCP server answers first - maybe the Linksys is faster???  From the sound of things (no crossover to connect), the router is also acting as switch?

---

### Post by mcgodx on 2009-06-05
> **Iowan said:**
> The machine will respond to whichever DHCP server answers first - maybe the Linksys is faster???  From the sound of things (no crossover to connect), the router is also acting as switch?

Well it's a wireless access point with a 4 port switch on it.  DHCP has been disabled on it.

To test, I changed the range on the Linksys, and the machines promptly changed their IP addresses with a release and renew.

---

