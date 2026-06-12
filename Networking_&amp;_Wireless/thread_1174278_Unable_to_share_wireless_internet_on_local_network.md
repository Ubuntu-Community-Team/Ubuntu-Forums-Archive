---
title: "Unable to share wireless internet on local network."
date: 2009-05-30
forum: Networking &amp; Wireless
---

### Post by Chris_no on 2009-05-30
I have gotten an old server to play with and have installed ubuntu server 9.04 on it. I have connected this to my main desktops network card eth0 (Hardy 8.04) through a hub. This works and they can access through ssh etc.

My main desktop have internet through wireless card wlan0.

I have tried to share the connection with advice like this

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

and this

[http://tldp.org/HOWTO/Masquerading-Simple-HOWTO/index.html](http://tldp.org/HOWTO/Masquerading-Simple-HOWTO/index.html)

and this 

[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

Here are some useful info.

ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:00:e8:e4:40:dd  
          inet addr:192.168.*.*  Bcast:192.168.*.255  Mask:255.255.255.0
          inet6 addr: ****::200:e8ff:fee4:****/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:33183 (32.4 KB)  TX bytes:52648 (51.4 KB)
          Interrupt:17 Base address:0xac00 

eth1      Link encap:Ethernet  HWaddr 00:16:17:b8:83:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56800 (55.4 KB)  TX bytes:56800 (55.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:11:95:47:16:20  
          inet addr:**.0.0.**  Bcast:***.***.0.255  Mask:255.255.255.0
          inet6 addr: ****::211:95ff:fe47:****/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7584 errors:29 dropped:0 overruns:0 frame:0
          TX packets:5496 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4407851 (4.2 MB)  TX bytes:760895 (743.0 KB)
          Interrupt:18 Base address:0xc000
```

iptables -L

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  192.168.*.0/24       anywhere            state NEW 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

netstat -nr

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
**.0.0.0        0.0.0.0         255.255.255.0   U         0 0          0 wlan0
192.168.*.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
***.***.*.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         **.0.0.***      0.0.0.0         UG        0 0          0 wlan0
```

sysctl -p

```
kernel.printk = 4 4 1 7
kernel.maps_protect = 1
fs.inotify.max_user_watches = 524288
vm.mmap_min_addr = 65536
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.ip_forward = 1
vm.swappiness = 10
net.ipv4.conf.default.forwarding = 1
net.ipv4.conf.all.forwarding = 1
```

cat /etc/network/interfaces

```
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.*.*
netmask 255.255.255.0

auto eth0

iface wlan0 inet dhcp
wireless-key ********
wireless-essid ********

auto wlan0

```

lshw -C network

```
 *-network:0             
       description: Ethernet interface
       product: RTL-8029(AS)
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:01:07.0
       logical name: eth0
       version: 00
       serial: 00:00:**:**:**:**
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical
       configuration: broadcast=yes driver=ne2k-pci driverversion=1.03 ip=192.168.*.* latency=0 module=ne2k_pci multicast=yes
  *-network:1
       description: Wireless interface
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wlan0
       version: 00
       serial: 00:**:**:**:**:**
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci ip=*.0.0.* latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+

```

Can anyone spot what I have missed?

---

### Post by Iowan on 2009-05-30
[Here]("http://ubuntuforums.org/showthread.php?p=7371283#post7371283") is a thread concerning two active interfaces.
BTW, did you see/try the [wireless]("https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless") link at the bottom of the ICS help page... or is that one the wrong way around?

---

### Post by Chris_no on 2009-05-31
Just tried

```
sudo route add default gw *.0.0.* wlan0
```

from here
[http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

when i do

/etc/init.d/networking restart

i get

```
 * Reconfiguring network interfaces...                                                                                                                       RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.wlan0.pid with pid 5966
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:**:**:**:**:**
Sending on   LPF/wlan0/00:**:**:**:**:**
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to *.0.0.* port 67
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:**:**:**:**:**
Sending on   LPF/wlan0/00:**:**:**:**:**
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPOFFER of *.0.0.* from *.0.0.*
DHCPREQUEST of *.0.0.* on wlan0 to 255.255.255.255 port 67
DHCPACK of *.0.0.* from *.0.0.*
bound to *.0.0.* -- renewal in 33605 seconds.
```

I assume that it is the router ( *.0.0.* ) I need to set default route to and not my wlan0 ( *.0.0.* ).

However having done this when i do ping *.0.0.* or *** from the other computer i get. 

connect: Network is unreachable

And likevise apt-get update fails.

Will now look into wireless link here.
[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

---

### Post by Chris_no on 2009-05-31
Ah yes that is the wrong way round.

The two devices don't conflict. Internet stays up when eth0 is active.

I'm basically stuck figuring out why iptables wont let me through.

---

### Post by Chris_no on 2009-05-31
netstat -nr now shows

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
*.0.0.0        0.0.0.0         255.255.255.0   U         0 0          0 wlan0
192.168.*.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
***.***.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         **.0.0.***      0.0.0.0         UG        0 0          0 wlan0
0.0.0.0         **.0.0.***      0.0.0.0         UG        0 0          0 wlan0
```

It seems to me that the route command made a double gateway.
So I deleted it and tried.

> route add default gw *.0.0.*** eth0

This brought me

SIOCADDRT: No such process

The same with

> route add default gw **.0.0.* eth0

So that is a dead end.

---

### Post by Chris_no on 2009-05-31
I have also tried out this guide to no effect...

[http://ubuntuforums.org/showthread.php?t=713874](http://ubuntuforums.org/showthread.php?t=713874)

Every time I see a new guide I get some new pieces, but still no connection.

What I now did was to edit /etc/dhcp3/dhcpd.conf

It is like this now

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
option domain-name "*****";
option domain-name-servers *.0.0.***;

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

subnet 192.168.*.0 netmask 255.255.255.0 {
  range 192.168.*.* 192.168.*.*;
  option routers 192.168.*.0;
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
```

and /etc/default/dhcp3-server

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

This changed my other computers /etc/resolv.conf automatically

From this

domain byteworld
search byteworld
nameserver 127.0.0.1

to this

domain byteworld
search byteworld
nameserver *.0.0.*

But still no internet...

---

### Post by superprash2003 on 2009-05-31
are the machines able to ping the main computer?

---

### Post by Chris_no on 2009-05-31
Sure!
It all stops inside my desktop computer somewhere between
eth0 and wlan0.

In iptables I belive.

```
chris@byteserv:~$ ping 192.168.*.*
PING 192.168.1.1 (192.168.*.*) 56(84) bytes of data.
64 bytes from 192.168.*.*: icmp_seq=1 ttl=64 time=0.491 ms
64 bytes from 192.168.*.*: icmp_seq=2 ttl=64 time=0.411 ms
64 bytes from 192.168.*.*: icmp_seq=3 ttl=64 time=0.406 ms
64 bytes from 192.168.*.*: icmp_seq=4 ttl=64 time=0.404 ms
64 bytes from 192.168.*.*: icmp_seq=5 ttl=64 time=0.396 ms
64 bytes from 192.168.*.*: icmp_seq=6 ttl=64 time=0.420 ms
64 bytes from 192.168.*.*: icmp_seq=7 ttl=64 time=0.414 ms
64 bytes from 192.168.*.*: icmp_seq=8 ttl=64 time=0.420 ms
64 bytes from 192.168.*.*: icmp_seq=9 ttl=64 time=0.442 ms
64 bytes from 192.168.*.*: icmp_seq=10 ttl=64 time=0.406 ms
^C
--- 192.168.*.* ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 8996ms
rtt min/avg/max/mdev = 0.396/0.421/0.491/0.026 ms

```

---

### Post by Chris_no on 2009-06-01
Okay I have crawled deeper into the rabbithole by starting to read this.

[http://tldp.org/HOWTO/Adv-Routing-HOWTO/](http://tldp.org/HOWTO/Adv-Routing-HOWTO/)

I've now done this.

> echo 200 **** >> /etc/iproute2/rt_tables

And made this script in /etc/network/if-up.d/

```
#!/bin/bash
#Setting up my network route

ip rule add from 192.168.*.* table byteroute

ip route add default via *.0.0.* dev wlan0 table byteroute
ip route flush cache
```

But no connection to internet still.

---

### Post by Chris_no on 2009-06-01
Wow unexpected development.

It seems the line in my script 

> ip rule add from 192.168.*.* table byteroute

was wrongly placed cause now every time I restart networking
a new rule is added. This killed my connection to the new machine.

ip rule ls

```
0:	from all lookup local 
32756:	from 192.168.*.* lookup ***route 
32757:	from 192.168.*.* lookup ***route 
32758:	from 192.168.*.* lookup ***route 
32759:	from 192.168.*.* lookup ***route 
32760:	from 192.168.*.* lookup ***route 
32761:	from 192.168.*.* lookup ***route 
32762:	from 192.168.*.* lookup ***route 
32763:	from 192.168.*.* lookup ***route 
32764:	from 192.168.*.* lookup ***route 
32765:	from 192.168.*.* lookup ***route 
32766:	from all lookup main 
32767:	from all lookup default 
```

Automated scripts can cause a headache if you tell them the wrong things.

It would probably be better if i put it in rc.local since I think the rules is wiped on reboot.

---

### Post by Chris_no on 2009-06-01
I have opened a thread on a Norwegian Linux forum linux1.no and on
linuxquestions.org to maybe find someone who can figure this out.

[http://linux1.no/forum/viewtopic.php?f=226&t=221663](http://linux1.no/forum/viewtopic.php?f=226&t=221663)

[http://www.linuxquestions.org/questions/linux-networking-3/tricky-internet-sharing-problem.-729801/#post3558774](http://www.linuxquestions.org/questions/linux-networking-3/tricky-internet-sharing-problem.-729801/#post3558774)

---

### Post by Chris_no on 2009-06-01
HORRAY PROBLEM SOLVED!!!

As always it was something stupid.

Me being CERTAIN that the problem was at the host
forgot all about the fact that my poor little client
needed a default gateway.

No wonder I didn't find anything. But could ping in and out.

> route add default gw 192.168.*.*

solved everything.

Hope I can be an example for others to learn from... ;)

---

