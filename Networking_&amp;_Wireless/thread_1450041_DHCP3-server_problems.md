---
title: "DHCP3-server problems"
date: 2010-04-08
forum: Networking &amp; Wireless
---

### Post by jbrown96 on 2010-04-08
I'm trying to test out a Thin client setup, but I cannot seem to get DHCPD running at all. 

Background: I'm experienced with Linux and have configured dhcpd on a Fedora workstation but never ltsp. 

Ubuntu seemed to be the easiest Distro to use; I have a lot of expereience with it and there's an install option from the alternate CD that installs a "ltsp server." I used Beta1 of 10.04, but I have installed the standalone packages (ltsp-server-standalone) in 9.10 as well (I have the same problem in both).

When installation (from the alt. cd) finishes, there is a warning that I need to add my interface to /etc/ltsp/dhcpd.conf. 

So I boot up the system and open up that file, which contains
```

#
# Default LTSP dhcpd.conf config file.
#

authoritative;

subnet 192.168.0.0 netmask 255.255.255.0 {
    interface eth0;
    range 192.168.0.20 192.168.0.250;
    option domain-name "example.com";
    option domain-name-servers 192.168.0.1;
    option broadcast-address 192.168.0.255;
    option routers 192.168.0.1;
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
The only thing that I changed was adding the "interface eth0;" line; I also tried adding in a host declaration to the end of the file. 
Code:
host ltsp {
hardware ethernet XX:XX:XX:XX:XX:XX;
fixed-address 192.168.0.1;
}


I also modified /etc/default/dhcp3-server to have 
```

INTERFACES="eth0"

```

If you look at /etc/init.d/dhcp3-server, you can see that if /etc/ltsp/dhcpd.conf exists, then that config is used instead of /etc/dhcp3/dhcpd.conf. I have tried removing /etc/ltsp/dhcpd.conf and working directly with /etc/dhcp3/dhcpd.conf that is (I have removed a lot of the commented-out examples)
```

ddns-updates off;
option T150 code 150 = string;
deny client-updates;
one-lease-per-client false;
allow bootp;
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.

# option definitions common to all supported networks...
option domain-name "example.org";
option domain-name-servers ns1.example.org, ns2.example.org;

default-lease-time 600;
max-lease-time 7200;
authoritative;

# This is a very basic subnet declaration.

subnet 192.168.0.0 netmask 255.255.255.0 {
  interface eth0;
  range 192.168.0.1 192.168.0.255;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
}

```
This doesn't work either; I get the same error. However, this is exactly the same as my dhcpd.conf on my Fedora workstation (except I use 10.0.0.X address space), which works perfectly. 

Error:
Here's what I get no matter what changes I have made
Code:
```

sudo service dhcp3-server start
* Starting DHCP server dhcpd3                                                                                                                        * check syslog for diagnostics.
[fail]

```

Here's syslog
```

Apr  7 15:00:19 helios dhcpd: Internet Systems Consortium DHCP Server V3.1.2
Apr  7 15:00:19 helios dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Apr  7 15:00:19 helios dhcpd: All rights reserved.
Apr  7 15:00:19 helios dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Apr  7 15:00:20 helios dhcpd: Internet Systems Consortium DHCP Server V3.1.2
Apr  7 15:00:20 helios dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Apr  7 15:00:20 helios dhcpd: All rights reserved.
Apr  7 15:00:20 helios dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Apr  7 15:00:20 helios dhcpd: Wrote 0 leases to leases file.
Apr  7 15:00:20 helios dhcpd: 
Apr  7 15:00:20 helios dhcpd: No subnet declaration for eth0 (0.0.0.0).
Apr  7 15:00:20 helios dhcpd: ** Ignoring requests on eth0.  If this is not what
Apr  7 15:00:20 helios dhcpd:    you want, please write a subnet declaration
Apr  7 15:00:20 helios dhcpd:    in your dhcpd.conf file for the network segment
Apr  7 15:00:20 helios dhcpd:    to which interface eth0 is attached. **
Apr  7 15:00:20 helios dhcpd: 
Apr  7 15:00:20 helios dhcpd: 
Apr  7 15:00:20 helios dhcpd: Not configured to listen on any interfaces!

```
What's wrong with my dhcp server? Thanks for the help.

---

### Post by pavel989 on 2010-04-09
what ur interfaces file look like?

---

