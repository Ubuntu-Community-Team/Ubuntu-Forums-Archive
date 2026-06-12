---
title: "I broke DHCP3-server"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by pepsifx357 on 2010-11-15
Hey guys, I had a server attached to a laptop via ethernet or eth0.  On the laptop I had the ethernet card share the wireless internet connection with the server.

I somehow managed to remove the dhcp server and cannot get it back.  I've reinstalled dhcp3-server and here is what I get on the laptop:

```
ben@ben-laptop:~$ sudo /etc/init.d/dhcp3-server restart
[sudo] password for ben: 
 * Stopping DHCP server dhcpd3                                           [fail] 
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]
ben@ben-laptop:~$
```

Here is the output of syslog:

```
 Nov 15 11:17:29 ben-laptop dhcpd: No subnet declaration for eth1 (0.0.0.0).
Nov 15 11:17:29 ben-laptop dhcpd: ** Ignoring requests on eth1.  If this is not what
Nov 15 11:17:29 ben-laptop dhcpd:    you want, please write a subnet declaration
Nov 15 11:17:29 ben-laptop dhcpd:    in your dhcpd.conf file for the network segment
Nov 15 11:17:29 ben-laptop dhcpd:    to which interface eth1 is attached. **
Nov 15 11:17:29 ben-laptop dhcpd: 
Nov 15 11:17:29 ben-laptop dhcpd: 
Nov 15 11:17:29 ben-laptop dhcpd: Not configured to listen on any interfaces!

```

I messed around with the /etc/dhcp3/dhcpd.conf and the /etc/default/dhcp3-server files.  Obviously I screwed up.

I'm not sure what to do here...

Thanks

---

### Post by pepsifx357 on 2010-11-15
Here is a copy of my ifconfig:

```
ben@ben-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:63:9a:ea:4c  
          inet6 addr: fe80::21b:63ff:fe9a:ea4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26568 (26.5 KB)  TX bytes:3719 (3.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2509 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:636144 (636.1 KB)  TX bytes:636144 (636.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:b3:b9:6a:ab  
          inet addr:1.1.1.130  Bcast:1.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:b3ff:feb9:6aab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:40873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47533359 (47.5 MB)  TX bytes:5123400 (5.1 MB)

```

dhcp3.conf:

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
# ddns-update-style none;

# option definitions common to all supported networks...
# option domain-name "example.org";
# option domain-name-servers ns1.example.org, ns2.example.org;

# default-lease-time 600;
# max-lease-time 7200;
# option subnet-mask 255.255.255.0;
# option broadcast-address 192.168.1.255;
# option routers 192.168.1.254;
# option domain-name-servers 192.168.1.1, 192.168.1.2;
# option domain-name "mydomain.example";

# subnet 192.168.1.0 netmask 255.255.255.0 {
# range 192.168.1.10 192.168.1.100;
# range 192.168.1.150 192.168.1.200;
# } 

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
# authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
# log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

# subnet 10.152.187.0 netmask 255.255.255.0 {
# }

# This is a very basic subnet declaration.

# subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
# }

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
# }

# A slightly different configuration for an internal subnet.
subnet 10.5.5.0 netmask 255.255.255.224 {
  range 10.5.5.26 10.5.5.30;
  option broadcast-address 10.5.5.31;
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

dhcp3-server:

```
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

---

### Post by sikander3786 on 2010-11-15
Hi.

dhcpd.conf seems ok to me.

What I would do first of all is to check if eth0 is actually connected. I mean the ethernet cable is plugged in and if it is connected to a switch or router, that router is powered on.

---

### Post by pepsifx357 on 2010-11-15
Yeah but even without anything connected, shouldn't the server start without failing?

---

### Post by sikander3786 on 2010-11-15
> **pepsifx357 said:**
> Yeah but even without anything connected, shouldn't the server start without failing?
No it wouldn't. It would fail if the link is down. At least that is what I've experienced.

---

### Post by pepsifx357 on 2010-11-15
Ok,  I hooked the laptop(DHCP Server) to the client and this is what I got.

```
ben@ben-laptop:~$ sudo /etc/init.d/dhcp3-server restart
[sudo] password for ben: 
 * Stopping DHCP server dhcpd3                                           [fail] 
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]
```

syslog

```
Nov 15 13:21:47 ben-laptop dhcpd: Wrote 0 leases to leases file.
Nov 15 13:21:47 ben-laptop dhcpd: 
Nov 15 13:21:47 ben-laptop dhcpd: No subnet declaration for eth0 (0.0.0.0).
Nov 15 13:21:47 ben-laptop dhcpd: ** Ignoring requests on eth0.  If this is not what
Nov 15 13:21:47 ben-laptop dhcpd:    you want, please write a subnet declaration
Nov 15 13:21:47 ben-laptop dhcpd:    in your dhcpd.conf file for the network segment
Nov 15 13:21:47 ben-laptop dhcpd:    to which interface eth0 is attached. **
Nov 15 13:21:47 ben-laptop dhcpd: 
Nov 15 13:21:47 ben-laptop dhcpd: 
Nov 15 13:21:47 ben-laptop dhcpd: Not configured to listen on any interfaces!

```

By the way, I was messing around and found an LTSP server tutorial which installed another dhcp config file which is located under /etc/ltsp/dhcpd.conf

It looks like this:

```
#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 1.1.1.0 netmask 255.255.255.0 {
    range 1.1.1.200 1.1.1.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.1.254;
    option broadcast-address 1.1.1.130;
    option routers 1.1.1.1;
#    next-server 192.168.0.1;
#    get-lease-hostnames true;
    option subnet-mask 255.255.255.0;
    option root-path "/opt/ltsp/i386";
    if substring( option vendor-class-identifier, 0, 9 ) = "PXEClient" {
        filename "/ltsp/i386/pxelinux.0";
    } else {
        filename "/ltsp/i386/nbi.img";
    }
}
```

---

### Post by sikander3786 on 2010-11-15
Did you assign a static IP to your eth0 interface?

Look under /etc/network/interfaces.

```
auto eth0
iface eth0 inet static
    address 10.5.5.1
    netmask 255.255.255.254
```

---

### Post by pepsifx357 on 2010-11-15
I was using DHCP.  I was also using the network manager to control the internet sharing with the wireless card and the eth0.

right now under /etc/network/interfaces there is only

auto lo
iface lo inet loopback

---

### Post by sikander3786 on 2010-11-15
Right click Network Manager > Edit Connections > Auto Eth0 > Edit > IPv4 Settings > Set method to manual and put in your IP and subnet mask.

Or edit /etc/network/interfaces and put these lines above the 2 already have in there.

```
auto eth0
iface eth0 inet static
    address 10.5.5.1
    netmask 255.255.255.254
```

Reboot and try starting dhcp3-server again.


Edit: I just noticed, 10.5.5.0 will be the network address for your network. Change it to 10.5.5.1 or whatever you prefer except 10.5.5.0 in your dhcpd.conf as well in interfaces. I have updated the post for that.

---

### Post by pepsifx357 on 2010-11-16
no matter what I do, it keeps saying the same thing.

```
Nov 16 08:40:38 ben-laptop dhcpd: Wrote 0 leases to leases file.
Nov 16 08:40:38 ben-laptop dhcpd: 
Nov 16 08:40:38 ben-laptop dhcpd: No subnet declaration for eth0 (0.0.0.0).
Nov 16 08:40:38 ben-laptop dhcpd: ** Ignoring requests on eth0.  If this is not what
Nov 16 08:40:38 ben-laptop dhcpd:    you want, please write a subnet declaration
Nov 16 08:40:38 ben-laptop dhcpd:    in your dhcpd.conf file for the network segment
Nov 16 08:40:38 ben-laptop dhcpd:    to which interface eth0 is attached. **
Nov 16 08:40:38 ben-laptop dhcpd: 
Nov 16 08:40:38 ben-laptop dhcpd: 
Nov 16 08:40:38 ben-laptop dhcpd: Not configured to listen on any interfaces!

```

I even tried to delete the auto eth0 or "Wired Connection" from the network manager and see if that cleared it up.  Is this a bug or something?

---

### Post by pepsifx357 on 2010-11-16
Unfortunately I had to reinstall Ubuntu.  I couldn't for the life of me find the problem let alone the solution online.:confused:  I'm not sure if I didn't confused the dhcp server to the point where there was no fixing it, but all is well now.  Hope no one else runs into this problem. :)

---

