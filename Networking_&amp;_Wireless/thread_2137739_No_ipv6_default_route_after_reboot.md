---
title: "No ipv6 default route after reboot"
date: 2013-04-21
forum: Networking &amp; Wireless
---

### Post by brokenflea on 2013-04-21
Hello All,

I've been trying to figure this one out for the most of this weekend and banging my head against the wall. Google search doesn't seem to yield anything. 
I'm running a fresh install of 12.04 (64 bit). 
I have a tunnel from HE.net, the tunnel comes up fine, and I can resolve v6 resources. However, on a reboot, my default route disappears and I've had to add it in manually from CLI

```

$ ping6 ipv6.google.com
unknown host

$ netstat -6rn
Kernel IPv6 routing table
Destination                    Next Hop                   Flag Met Ref Use If
2001:470:39:18::2/128          ::                         U    1024 0     0 he-ipv6
2001:470:39:18::/64            ::                         Un   256 0     0 he-ipv6
2001:470:4b:18::/64            ::                         U    256 0     0 eth0
fe80::/64                      ::                         U    256 0     0 eth0
fe80::/64                      ::                         Un   256 0     0 he-ipv6
::/0                           ::                         U    1024 0     0 he-ipv6
::/0                           ::                         !n   -1  1   143 lo
::1/128                        ::                         Un   0   1     5 lo
2001:470:39:18::/128           ::                         Un   0   1     0 lo
2001:470:39:18::2/128          ::                         Un   0   1     1 lo
2001:470:4b:18::/128           ::                         Un   0   1     0 lo
fe80::/128                     ::                         Un   0   1     0 lo
fe80::a0a:ab50/128             ::                         Un   0   1     0 lo
fe80::a60:6eff:fe81:4f26/128   ::                         Un   0   1     3 lo
ff00::/8                       ::                         U    256 0     0 eth0
ff00::/8                       ::                         U    256 0     0 he-ipv6
::/0                           ::                         !n   -1  1   143 lo

~$ sudo ip route add ::/0 dev he-ipv6

$ ping6 ipv6.google.com
PING ipv6.google.com(den03s05-in-x11.1e100.net) 56 data bytes
64 bytes from den03s05-in-x11.1e100.net: icmp_seq=1 ttl=53 time=81.1 ms
64 bytes from den03s05-in-x11.1e100.net: icmp_seq=2 ttl=53 time=81.1 ms
^C
--- ipv6.google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 81.154/81.155/81.157/0.284 ms

```

I've configured /etc/network/interfaces to have the default route come up after a reboot, however, it doesn't seem to stick it seems.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
	address 10.10.171.80
	netmask 255.255.255.0
	gateway 10.10.171.1 
	dns-nameservers 127.0.0.1
	dns-search b.lan
	dns-domain b.lan
auto he-ipv6
iface he-ipv6 inet6 v4tunnel
	address 2001:470:39:18::2
	netmask 64
	endpoint 184.105.250.46
	local 10.10.171.80
	ttl 225
	gateway 2001:470:39:18::2
	post-up /sbin/ip -6 route add ::/0 dev he-ipv6
	pre-down /sbin/ip -6 route del ::/0 dev he-ipv6
iface eth0 inet6 static
	address 2001:470:4b:18::
	netmask 64
	#gateway 2001:470:39:18::1
	dns-nameservers 2001:4860:4860::8888 2001:4860:4860::8844

```


If someone could point me in the right direction on how to troubleshoot, I would really appreciate it. 

TIA.

---

### Post by brokenflea on 2013-04-21
figured it out. 
removed
 
```

gateway 2001:470:39:18::2

```

from /etc/network/interfaces and that seems to have done the trick.

---

### Post by midnightramen on 2013-04-21
if you are using the network connections / network manager applet, there is a section for IPv6 that may of help. Otherwise, from the command line, you may be able to add an entry in /etc/network/if-up.d and see if that works for you.

---

