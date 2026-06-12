---
title: "IP Routing/Forwarding Puzzle: Can't get it to work. Tried a lot of things"
date: 2011-11-06
forum: Networking &amp; Wireless
---

### Post by radarman on 2011-11-06
So, I am trying to use my ubuntu box as a router on my home LAN. I used to do it successfully with 10.x versions. I've put together a new box, installed 11.10 x64 server, upgraded everything I could. I did enable IPv4-forwarding in /etc/sysctl.conf. I checked a lot of things and tried a lot of things, but can't get IP-forwarding to work, and I miss it! :( When clients connect to my ubuntu host they get dhcp info successfully and they can resolve DNS fine, but fail to ping or access anything outside the linux box.

The setup looks like this:

```

	 Internet
	     |
        [ dd-wrt  ]
        192.168.1.1
             |
             |
             |
     eth0: 192.168.1.2
     [ linux router  ]
     br0: 192.168.10.1
             |
             |
          laptops

```

My bridge has 4 ethernet ports, all on a single pci-e card:

```
root@tank:/# brctl show
bridge name	bridge id		STP enabled	interfaces
br0		8000.00e0ed110e82	no		eth1
							eth2
							eth3
							eth4

```

My ifconfig looks like this:

```
br0       Link encap:Ethernet  HWaddr 00:e0:ed:11:0e:82  
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:edff:fe11:e82/64 Scope:Link
          ...

eth0      Link encap:Ethernet  HWaddr bc:ae:c5:c1:f8:9c  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::beae:c5ff:fec1:f89c/64 Scope:Link
          ...

eth1      Link encap:Ethernet  HWaddr 00:e0:ed:11:0e:82  
          ...

eth2      Link encap:Ethernet  HWaddr 00:e0:ed:11:0e:83  
          ...

eth3      Link encap:Ethernet  HWaddr 00:e0:ed:11:0e:84  
          ...

eth4      Link encap:Ethernet  HWaddr 00:e0:ed:11:0e:85  
          ...

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          ...

```

My routing table is like this:

```
root@tank:/# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 br0

```

My iptables look like this:

```
root@tank:/# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Finally, here is my /etc/sysctl.conf. You can see that I enabled ipv4 routing and tried to disable anything IPv6:

```
root@tank:/# cat /etc/sysctl.conf 
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See /etc/sysctl.d/ for additional system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com

# Uncomment the following to stop low-level messages on console
#kernel.printk = 3 4 1 3

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next two lines to enable Spoof protection (reverse-path filter)
# Turn on Source Address Verification in all interfaces to
# prevent some spoofing attacks
#net.ipv4.conf.default.rp_filter=1
#net.ipv4.conf.all.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
# See http://lwn.net/Articles/277146/
# Note: This may impact IPv6 TCP sessions too
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

# Uncomment the next line to enable packet forwarding for IPv6
#  Enabling this option disables Stateless Address Autoconfiguration
#  based on Router Advertisements for this host
net.ipv6.conf.all.forwarding=0


###################################################################
# Additional settings - these settings can improve the network
# security of the host and prevent against some network attacks
# including spoofing attacks and man in the middle attacks through
# redirection. Some network environments, however, require that these
# settings are disabled so review and enable them as needed.
#
# Do not accept ICMP redirects (prevent MITM attacks)
#net.ipv4.conf.all.accept_redirects = 0
#net.ipv6.conf.all.accept_redirects = 0
# _or_
# Accept ICMP redirects only for gateways listed in our default
# gateway list (enabled by default)
# net.ipv4.conf.all.secure_redirects = 1
#
# Do not send ICMP redirects (we are not a router)
#net.ipv4.conf.all.send_redirects = 0
#
# Do not accept IP source route packets (we are not a router)
#net.ipv4.conf.all.accept_source_route = 0
#net.ipv6.conf.all.accept_source_route = 0
#
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

```

So I am at a loss! Why is my routing not working? :( Help!

---

### Post by radarman on 2011-11-07
Ok, figured it out. DD-WRT needed a static route for 192.168.10.0 subnet.

---

