---
title: "DHCP client on network does not seem to recognize that it is being sent a DHCPOFFER"
date: 2011-02-27
forum: Networking &amp; Wireless
---

### Post by taeksosin on 2011-02-27
Hi all, spent more hours than I care to mention attempting to solve this on my own utilizing the universal help file (google) and I still haven't had any luck getting things to work properly.  

Long story short, I have a classroom lab with 30 computers (Edubuntu 10.04, all updates applied) all tied into a series of switches.  Said switches then tie into the class server (Ubuntu Server 10.04, updates again).  On the class server, I've installed dhcp3-server and believe I've configured it correctly.  However, my clients are not receiving an IP from the server.  It looks like there's a disconnect of some variety between DHCPDISCOVER being sent from one of the clients, the DHCPOFFER that's sent back from the server.  

Here's a copy of my dhcpd.conf, interfaces, and the applicable output from /var/log/syslog from the server and the results of running sudo dhclient from one of the clients.  dhclient.conf on the client machines is stock.

If anyone can help, that would be great.  Oh, and thought I should mention this, I KNOW it's not the networking equipment because if I plug the internet line into the appropriate port on the main switch, all the client computers have web access just fine.

Edit: Forgot to mention, the dhcp3-server appears to come up just fine when running /etc/init.d/dhcp3-server restart

Output from /var/log/syslog from the server
```

Feb 27 12:30:00 CCALabServer dhcpd: DHCPDISCOVER from 00:21:70:5a:7f:01 via eth1
Feb 27 12:30:01 CCALabServer dhcpd: DHCPOFFER on 192.168.10.20 to 00:21:70:5a:7f:01 via eth1
Feb 27 12:30:05 CCALabServer dhcpd: DHCPDISCOVER from 00:21:70:5a:7f:01 via eth1
Feb 27 12:30:05 CCALabServer dhcpd: DHCPOFFER on 192.168.10.20 to 00:21:70:5a:7f:01 via eth1
Feb 27 12:30:16 CCALabServer dhcpd: DHCPDISCOVER from 00:21:70:5a:7f:01 via eth1
Feb 27 12:30:16 CCALabServer dhcpd: DHCPOFFER on 192.168.10.20 to 00:21:70:5a:7f:01 via eth1
Feb 27 12:30:25 CCALabServer dhcpd: DHCPDISCOVER from 00:21:70:5a:7f:01 via eth1
Feb 27 12:30:25 CCALabServer dhcpd: DHCPOFFER on 192.168.10.20 to 00:21:70:5a:7f:01 via eth1
Feb 27 12:30:41 CCALabServer dhcpd: DHCPDISCOVER from 00:21:70:5a:7f:01 via eth1
Feb 27 12:30:41 CCALabServer dhcpd: DHCPOFFER on 192.168.10.20 to 00:21:70:5a:7f:01 via eth1
Feb 27 12:30:56 CCALabServer dhcpd: DHCPDISCOVER from 00:21:70:5a:7f:01 via eth1
Feb 27 12:30:56 CCALabServer dhcpd: DHCPOFFER on 192.168.10.20 to 00:21:70:5a:7f:01 via eth1
Feb 27 12:31:37 CCALabServer avahi-daemon[761]: server.c: Packet too short or invalid while reading response record. (Maybe a UTF-8 problem?)
```contents of dhpcd.conf from server
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
#option domain-name "CCALab.local";
#option domain-name-servers 8.8.8.8, 8.8.4.4;

default-lease-time 600;
max-lease-time 7200;

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

subnet 192.168.10.0 netmask 255.255.255.0 {
  range 192.168.10.20 192.168.10.29;
  option subnet-mask 255.255.255.0;
  option broadcast-address 192.168.10.255;
  option domain-name-servers 8.8.8.8, 8.8.4.4;
  option routers 192.168.10.1;
host Bell {
hardware ethernet 00:21:70:5A:7A:03;
fixed-address 192.168.10.29;
}

host Edison {
hardware ethernet 00:21:70:5A:6B:A6;
fixed-address 192.168.10.30;
}

host Gutenberg {
hardware ethernet 00:21:70:5A:69:93;
fixed-address 192.168.10.31;
}

host Lewis {
hardware ethernet 00:21:70:5A:7F:F8;
fixed-address 192.168.10.32;
}

host Chaucer {
hardware ethernet 00:21:70:5A:7E:FE;
fixed-address 192.168.10.33;
}

host Shakespear {
hardware ethernet 00:21:70:5A:7D:85;
fixed-address 192.168.10.34;
}

host Alexander {
hardware ethernet 00:21:70:5A:78:81;
fixed-address 192.168.10.35;
}

host Napoleon {
hardware ethernet 00:21:70:5A:7E:F6;
fixed-address 192.168.10.36;
}

host Hannibal {
hardware ethernet 00:21:70:5A:6C:FD;
fixed-address 192.168.10.37;
}

host Aristotle {
hardware ethernet 00:21:70:5A:7F:07;
fixed-address 192.168.10.38;
}

host Socrates {
hardware ethernet 00:21:70:5A:7F:07;
fixed-address 192.168.10.39;
}

host Confucious {
hardware ethernet 00:21:70:5A:6B:36;
fixed-address 192.168.10.40;
}

host Michelangelo {
hardware ethernet 00:21:70:5A:75:E1;
fixed-address 192.168.10.41;
}

host DaVinci {
hardware ethernet 00:21:70:5A:7A:C7;
fixed-address 192.168.10.42;
}

host Rembrandt {
hardware ethernet 00:21:70:5A:79:09;
fixed-address 192.168.10.43;
}

host Curie {
hardware ethernet 00:21:70:5A:72:69;
fixed-address 192.168.10.44;
}

host Tesla {
hardware ethernet 00:21:70:5A:76:5A;
fixed-address 192.168.10.45;
}

host Einstein {
hardware ethernet 00:21:70:5A:7E:AC;
fixed-address 192.168.10.46;
}

host Newton {
hardware ethernet 00:21:70:5A:7E:FC;
fixed-address 192.168.10.47;
}

host MarcoPolo {
hardware ethernet 00:21:70:2A:27:B6;
fixed-address 192.168.10.48;
}

host Ericson {
hardware ethernet 00:21:70:5A:7E:03;
fixed-address 192.168.10.49;
}

host Magellan {
hardware ethernet 00:21:70:5A:7E:85;
fixed-address 192.168.10.50;
}

host Bach {
hardware ethernet 00:21:70:5A:7E:83;
fixed-address 192.168.10.51;
}

host Mozart {
hardware ethernet 00:21:70:5A:7E:B1;
fixed-address 192.168.10.52;
}

host Beethoven {
hardware ethernet 00:21:70:5A:7B:4E;
fixed-address 192.168.10.53;
}

host Nightengale {
hardware ethernet 40:61:86:18:C7:67;
fixed-address 192.168.10.54;
}

host Fleming {
hardware ethernet 40:61:86:18:9A:53;
fixed-address 192.168.10.55;
}

host Salk {
hardware ethernet 40:61:86:18:99:B0;
fixed-address 192.168.10.56;
}

}

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

```Output from dhclient on client machine
```

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.

```Contents of /etc/network/interfaces on server
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 192.168.10.1
netmask 255.255.255.0
up route add -host 255.255.255.255 eth1

```Contents of /etc/default/dhcp3-server
```

# Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#    Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth1"

```Output of ifconfig on server
```

eth0      Link encap:Ethernet  HWaddr 00:01:2e:2f:7f:98  
          inet addr:192.168.2.40  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2eff:fe2f:7f98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1750 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5233640 (5.2 MB)  TX bytes:274589 (274.5 KB)
          Interrupt:27 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:0e:c6:88:37:f9  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:c6ff:fe88:37f9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56 errors:120 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:121196 (121.1 KB)  TX bytes:11930 (11.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1784 (1.7 KB)  TX bytes:1784 (1.7 KB)

```

---

