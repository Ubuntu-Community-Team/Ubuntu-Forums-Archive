---
title: "Ubuntu as router -- a painful road, please help"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by littlegreenman on 2009-02-17
Hello,
I've been trying to set up my ubuntu machine as the server for my small business office. We have 13 PCs altogether. In the meantime I created a smaller network consisting of my new ubuntu server and another laptop, connected via an Ethernet wire so that I test all the settings.

So, how I want my small testing network to be?

Ubuntu machine connected to internet via eth3.
eth3 gets all the information from router via dhcp.

Ubuntu machine has eth0 card. this is the card where I connect the laptop.
Ubuntu routes the connections between eth0 and eth3.
Ubuntu has DHCP server so it gives automatically all the info to the connected laptop.

Laptop connects via eth0 to Ubuntu machine and gets everything automatically via dhcp.

Laptop has Ubuntu installed.

I am able to connect to the network with the laptop, but when I try to ping the router ubuntu machine it does not work, and can't ping any ip address for that matter.

So, I am a bit of a newbie, sorry if any of the language is not very computerish, and also I am not sure exactly what I should show you so you can help me, so here are some outputs and information I think might be useful. Thanks for all the help.

Outputs:

> $ uname -a
Linux servidor 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux


> $ ifconfig                                                       
br0       Link encap:Ethernet  HWaddr 00:21:91:ec:6e:37                            
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0           
          inet6 addr: fe80::221:91ff:feec:6e37/64 Scope:Link                       
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                       
          RX packets:1845 errors:0 dropped:0 overruns:0 frame:0                    
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0                    
          collisions:0 txqueuelen:0                                                
          RX bytes:179818 (179.8 KB)  TX bytes:5267 (5.2 KB)                       

eth0      Link encap:Ethernet  HWaddr 00:21:91:ec:6e:37  
          inet6 addr: fe80::221:91ff:feec:6e37/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1        
          RX packets:52873 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33376 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000                            
          RX bytes:68986129 (68.9 MB)  TX bytes:2892375 (2.8 MB)  
          Interrupt:19 Base address:0xc00                         

eth3      Link encap:Ethernet  HWaddr 00:00:6c:07:d4:4c  
          inet addr:192.168.2.109  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::200:6cff:fe07:d44c/64 Scope:Link              
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1              
          RX packets:27553 errors:0 dropped:0 overruns:0 frame:0          
          TX packets:10889 errors:0 dropped:0 overruns:0 carrier:0        
          collisions:0 txqueuelen:1000
          RX bytes:18499934 (18.4 MB)  TX bytes:1276940 (1.2 MB)
          Interrupt:220

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:684 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:35414 (35.4 KB)  TX bytes:35414 (35.4 KB)


/etc/network/interfaces:
> # Set up the local loopback interface
auto lo
iface lo inet loopback

# Set up the external interface
#
# Don't forget to change eth0 to the proper name of the external
# interface if applicable.
#

auto eth3
iface eth3 inet dhcp

# Set up the internal wired network
#
# Don't forget to change eht1 to the proper name of the internal
# wired network interface if applicable
#

auto eth0
iface eth0 inet static
    address 192.168.1.1
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255

# Set up the internal wired network
#
# It's not necessary to bring this interface up as the bridge
# we are about to create does this. Leave these lines commented.
#
#auto eth3
#iface eth3 inet manual

# Set up the internal wired network bridge
#
# Don't forget to change eth1 to the proper name of
# the internal wired interfaces if applicable.
#
auto br0
iface br0 inet static
    address 192.168.1.1
    network 192.168.1.0
    netmask 255.255.255.0
    broadcast 192.168.1.255
    bridge-ports eth0


/etc/dhcp3/dhcpd.conf:
> #
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
range 192.168.1.100 192.168.1.200;
option domain-name-servers 212.113.164.57, 212.113.164.56, 212.113.164.49, 212.113.164.48;
option domain-name "netcabo.pt";
option routers 192.168.2.1;
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

/etc/default/dhcp3-server:
> # Defaults for dhcp initscript
# sourced by /etc/init.d/dhcp
# installed at /etc/default/dhcp3-server by the maintainer scripts

#
# This is a POSIX shell fragment
#

# On what interfaces should the DHCP server (dhcpd) serve DHCP requests?
#	Separate multiple interfaces with spaces, e.g. "eth0 eth1".
INTERFACES="eth0"

---

### Post by Vesperatus on 2009-02-17
I'm not sure, but the netmask might be causing an issue here.

you have 192.168.1.0 on the eth0 side with a netmask of 255.255.255.0 and 192.168.2.0 on the eth3 side with a netmask of 255.255.255.0.  I'm not familiar with the bridge, but since your dhcpd server gives a router of 192.168.2.1, anything on the 192.168.1.0 will not be able to reach that ip. 

I hope other people will look at that cause I only took a quick look at your config. Try changing the netmask with this line in your dhcpd.conf :

```
option subnet-mask              255.255.0.0;
```

---

### Post by superprash2003 on 2009-02-17
remove the broadcast and network lines of eth0 and restart networking ( sudo /etc/init.d/networking restart) your ifconfig output shows eth0 not getting the 192.168.1.1 ip.. thats where the problem lies..

---

