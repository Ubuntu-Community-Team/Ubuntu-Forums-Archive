---
title: "Internal Network Issue"
date: 2011-04-06
forum: Networking &amp; Wireless
---

### Post by nethompson on 2011-04-06
I could really use some help on this. This is my first time posting so I will try to do my best. I am trying to setup a dhcp server for my internal network. I have two NICs, a modem, and a wireless router. I have my server connected directly to my modem which is providing me with Internet access on eth1 and is working fine. I have dhcp and dns setup on eth0 which is connected to my router. The router shows that it is connected to the Internet but when the router gives a client computer an IP address, the client is unable to connect to the Internet but can connect to the router. I will post my configuration files below with my current configuration.

[SIZE=4](NOTE THAT EVERYTHING WITH "Xs" are static, PUBLIC IPs ASSIGNED BY ISP) [/SIZE]

/etc/network/interfaces:
```

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
    address        192.168.0.1
    netmask        255.255.255.0
    broadcast    192.168.0.255
    network        192.168.0.0
    gateway        xx.xx.xxx.xxx  
auto eth1
iface eth1 inet static
    address         xx.xx.xxx.xxx   
    netmask        255.255.255.252
    broadcast     xx.xx.xxx.xxx
    network         xx.255.255.255
    gateway         xx.xx.xxx.xxx   

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth1 up # line maintained by pppoeconf
provider dsl-provider

auto eth1
```


/etc/default/dhcp3-server:
```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"
```


/etc/dhcp3/dhcpd.conf:
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
#option domain-name "example.org";
#option domain-name-servers 192.168.1.254;

#default-lease-time 86400;
#max-lease-time 604800;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.0.0.0 netmask 255.0.0.0 {
#  range 10.0.0.2 10.0.0.2;
#  option subnet-mask 255.0.0.0;
#  option broadcast-address 10.255.255.255;
#  option routers 192.168.1.254;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
subnet 192.168.0.0 netmask 255.255.255.0 {
  range 192.168.0.100 192.168.0.200;
  option domain-name-servers 192.168.0.1;
  option domain-name "nick-srv.local";
  option routers xx.xx.xxx.xxx;     
 option broadcast-address 192.168.0.255;
  default-lease-time 86400;
  max-lease-time 604800;
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
/etc/resolv.conf:
```

# Generated by NetworkManager
nameserver 205.152.37.23
nameserver 205.152.150.23
```


/etc/bind/named.conf.options:
```
options {
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you may need to fix the firewall to allow multiple
    // ports to talk.  See [http://www.kb.cert.org/vuls/id/800113](http://www.kb.cert.org/vuls/id/800113)

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

     forwarders {
         205.152.37.23;205.152.150.23;
     };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};

```


/etc/bind/named.conf:
```

// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the 
// structure of BIND configuration files in Debian, *BEFORE* you customize 
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local
zone "." {
        type hint;
        file "/etc/bind/db.root";
};
// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912
zone "nick-srv.local" { //change asus.local to whatever you named your domain such as mydomain.local
type master;
file "/etc/bind/zones/nick-srv.local.db"; //this file or foler does not exist so we will need to make it
};
zone "xxx.xx.xx.in-addr.arpa" {   
type master;
file "/etc/bind/zones/rev.xxx.xx.xx.in-addr.arpa";//this file does not exist so we will also need to make it
};
zone "localhost" {
        type master;
        file "/etc/bind/db.local";
};
zone "127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};
zone "0.in-addr.arpa" {
        type master;
        file "/etc/bind/db.0";
};
zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};

include "/etc/bind/named.conf.options";
include "/etc/bind/named.conf.local";
include "/etc/bind/named.conf.default-zones";
# Use with the following in named.conf, adjusting the allow list as needed:
 key "rndc-key" {
     algorithm hmac-md5;
     secret "bELH8IxCnbCaAyv9DQUk2w==";
 };
 
 controls {
     inet 127.0.0.1 port 953
         allow { 127.0.0.1; } keys { "rndc-key"; };
 };
# End of named.conf

```

/etc/bind/zones/nick-srv.local.db:
```

$ORIGIN .
$TTL 4000 ;
nick-srv.local.     IN SOA  server.nick-srv.local. admin.nick-srv.local. (
2007031001      ; serial
28800           ; refresh
3600            ; retry
604800          ; expire
38400           ; min
)
                NS      server.nick-srv.local.
$ORIGIN nick-srv.local.
                IN      A       xx.xx.xxx.xxx     
www             IN      A        xx.xx.xxx.xxx //an example
server          IN      A        xx.xx.xxx.xxx //an example
macpro          IN      A        xx.xx.xxx.xxx   //an example

```

/etc/bind/zones/rev.xxx.xx.xx.in-addr.arpa:
```

$ORIGIN .
$TTL 28800      ; 8 hours
xxx.xx.xx.IN-ADDR.ARPA IN SOA server.nick-srv.local. admin.nick-srv.local. (
                                2008110601 ; serial
                                28800      ; refresh (8 hours)
                                7200       ; retry (2 hours)
                                604800     ; expire (1 week)
                                86400      ; minimum (1 day)
                                )
                        NS      server.nick-srv.local.
$ORIGIN xxx.xx.xx.IN-ADDR.ARPA.
4                     PTR    macpro.nick-srv.local.
```


/etc/rc.local:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth1 -j MASQUERADE

exit 0
```

---

### Post by nosebreaker on 2011-04-06
Did you follow this guide: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Did you setup iptables?  If not then the boxes will be able to see the "router" linux box, but not the internet.

Also, the "router" linux box only has 1 gateway IP, whatever your ISP gives you.  Each client IP has a gateway IP of your linux router box.  Make sense?

---

### Post by nethompson on 2011-04-07
[SIZE=3]Thanks for your reply nosebreaker. I will check out the link you provided for me. However, will going through that setup mess up anything that I have already done? Either way it can be fixed, I would just like to know for reference. Also, I thought that I configured iptables but I may be mistaken. And for the gateway IP, the only one for my entire network, external and internal, would be the gateway that the ISP provided, correct?[/SIZE]

---

### Post by nethompson on 2011-04-09
Ok, I believe my issue with this has worsened. I had it working for a while. The power went out and now it no longer works. Everything has been left the same but when I do the route command this is what it gives me:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
adsl-065-012-17 *               255.255.255.255 UH    0      0        0 ppp0
70.159.160.82   *               255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         adsl-065-012-17 0.0.0.0         UG    0      0        0 ppp0

nick@nick-srv:/etc/dhcp3$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
public ip            0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
70.159.160.82   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         65.12.172.146   0.0.0.0         UG    0      0        0 ppp0


PLEASE HELP!!

---

### Post by nethompson on 2011-04-09
scratch the last post!!! I finally got it. The name server wasn't being applied to the resolv.conf file!!!

---

### Post by nosebreaker on 2011-04-11
Glad you got it working!

For future reference, the devices on the inside of your network should have the linux box as their gateway IP (so 192.168.0.1 in your case), the linux box should have a default gateway of 70.x.x.x (provided by your ISP).

To confirm if DNS is working or not, you can ping 4.2.2.2 (a easy-to-remember internet dns server), if that works but ping [www.google.com](www.google.com) does not, you know its DNS!

---

