---
title: "jaunty dhcp3 fails to start"
date: 2009-06-30
forum: Networking &amp; Wireless
---

### Post by bobwdn on 2009-06-30
I have been using Ubuntu since 6.06. Like it very much.

My latest install is Jaunty. This is a alternate CD install so I can run a LTSP system. During the install, jaunty complained about having to configure dhcp manually. (I did not note exactly what the message said, sorry.)

I thought dhcp should already be running. So when I do:
> /etc/init.d/dhcp3-server restart
 * Stopping DHCP server dhcpd3                                           [fail] 
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]

The syslog shows:

> grep dhcp /var/log/syslog
Jun 30 19:13:41 bob-desktop2 dhcpd: Internet Systems Consortium DHCP Server V3.1.1
Jun 30 19:13:41 bob-desktop2 dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Jun 30 19:13:41 bob-desktop2 dhcpd: All rights reserved.
Jun 30 19:13:41 bob-desktop2 dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 30 19:13:43 bob-desktop2 dhcpd: Internet Systems Consortium DHCP Server V3.1.1
Jun 30 19:13:43 bob-desktop2 dhcpd: Copyright 2004-2008 Internet Systems Consortium.
Jun 30 19:13:43 bob-desktop2 dhcpd: All rights reserved.
Jun 30 19:13:43 bob-desktop2 dhcpd: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Jun 30 19:13:43 bob-desktop2 dhcpd: Wrote 0 leases to leases file.
Jun 30 19:13:43 bob-desktop2 dhcpd: 
Jun 30 19:13:43 bob-desktop2 dhcpd: No subnet declaration for eth1 (0.0.0.0).
Jun 30 19:13:43 bob-desktop2 dhcpd: ** Ignoring requests on eth1.  If this is not what
Jun 30 19:13:43 bob-desktop2 dhcpd:    you want, please write a subnet declaration
Jun 30 19:13:43 bob-desktop2 dhcpd:    in your dhcpd.conf file for the network segment
Jun 30 19:13:43 bob-desktop2 dhcpd:    to which interface eth1 is attached. **
Jun 30 19:13:43 bob-desktop2 dhcpd: 
Jun 30 19:13:43 bob-desktop2 dhcpd: 
Jun 30 19:13:43 bob-desktop2 dhcpd: Not configured to listen on any interfaces!

As I no little about dhcp and it always worked fine in the past (past versions, that is) I need help. Suggestions?

---

### Post by Iowan on 2009-06-30
It appears that your interface is eth1, and it has no address. Please post results of **ifconfig**. Eventually, contents of */etc/dhcp3/dhcpd.conf* might be helpful.

---

### Post by bobwdn on 2009-07-01
ifconfig:

> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:2a:2f:4d  
          inet addr:192.168.242.120  Bcast:192.168.242.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe2a:2f4d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2029305 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2294546 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1363646755 (1.3 GB)  TX bytes:1829537373 (1.8 GB)
          Interrupt:252 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7244 (7.2 KB)  TX bytes:7244 (7.2 KB)

And the output from */etc/dhcp3/dhcpd.conf*:

> cat /etc/dhcp3/dhcpd.conf
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

Sorry, you may not have needed all of the */etc/dhcp3/dhcpd.conf*.

Now, for clarity, eth0 connects to the internet via my IPCop firewall that is running a dhcp server that issues the ip address based on the mac address of the eth0 (motherboard) lan. The eth1 is for LTSP client network connections. I have tried to set a static address for eth0 and than I am unable to connect to the internet. Then, I discovered that dhcp3-server will not start or stop. Could be a settings issue but, I am confused?

---

### Post by Iowan on 2009-07-02
I haven't (yet) done LTSP setup, so perhaps I don't understand how it is supposed to work, but for the DHCP server's I've set up, I need to have a subnet defined - in particular, in the same subnet (mask) as the interface that will be connecting to clients.

**ifconfig** shows eth1 as having no IP address.  It'll need one if it is to hand out DHCP addresses.

---

### Post by bobwdn on 2009-07-02
I agree. It is my understanding that dhcp3 assigns address for the LTSP network only and NOT the local LAN. (My local LAN is handled by my IPCop firewall machine.) I have a LTSP machine at work that is running 8.04.2LTS. Work is moving to a new location and I will not have time to look at it's setup until then. Give me a few days to look at these files on that "older" 8.04.2LTS computer. It may give more insight to my problem.

So, in a few days . . . . . .

---

### Post by shel-hall on 2009-07-05
I've just been wrestling with the same thing. 

I discovered that the DHCP server on the LTSP installation won't run unless the machine is assigned a static IP address, and you cannot assign a static IP address unless you ditch NetworkManager.

Once I got rid of NetworkManager and edited the various config files by hand (well, OK, with gedit), it seems to work fine.  dhcp3-server starts on bootup, clients get an IP address and a pointer to the LTSP server, the LTSP server serves up a boot image, the cliets boot and load Ubuntu, and all's right with the world.

-Shel

---

### Post by f.constantino on 2009-07-05
check your /etc/default/dhcp3-server file.

1. sudo gedit /etc/default/dhcp3-server

2. find this line: ... INTERFACES="" (by default it looks like this)

if you have something like INTERFACES="eth1" the dhcp3 server will be handling that interface and as previously mentioned, if you do want eth1 to manage adresses you will have to define a subnet for that interface, if you don't wish to have eth1 manage adresses put the /etc/default/dhcp3-server file back to its default state.

---

### Post by npnutn on 2009-07-07
I just manged to get dhcpd to start at boot by removing Network Manager and manually adding info to /etc/networking/interfaces.

---

