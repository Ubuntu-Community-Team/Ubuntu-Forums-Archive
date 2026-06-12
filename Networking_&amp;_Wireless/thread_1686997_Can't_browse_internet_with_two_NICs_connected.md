---
title: "Can't browse internet with two NICs connected"
date: 2011-02-13
forum: Networking &amp; Wireless
---

### Post by dhurler on 2011-02-13
I've got two onboard RTL8168 gigabit NICs that are connected to two different privately addressed networks. Eth0 is connected to a Linksys WRT54G router (running WRT-DD) and the router is NOT connected to the internet. Eth1 is connected to a Trendnet TEW-633GR router which IS connected to the internet via a DSL modem. Running Ubuntu 10.10 x64 fully updated with IPTABLES/firewall OFF.

Here is the setup:

eth0: IP address 192.168.1.201 mask 255.255.255.0 (no gateway set)
eth1: IP address 192.168.2.201 mask 255.255.255.0 gateway 192.168.2.1 DNS 8.8.8.8,8.8.4.4
  
routing table with both connections active:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0       U     1        0        0    eth1
192.168.1.0     *               255.255.255.0       U     1        0        0    eth0
link-local         *               255.255.0.0           U     1000   0        0   eth1
default           192.168.2.1     0.0.0.0            UG    0        0         0   eth1

I can't figure out why the "link-local" entry only appears for eth1. Why is it even being created? I was under the impression these entries were only created when a NIC was set for explicitly for "link-local" addressing or when it is set for DHCP and it can't grab an address.

this is the routing table with eth0 down:

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0      U     1          0        0   eth1
link-local         *               255.255.0.0          U     1000    0        0   eth1
default           192.168.2.1     0.0.0.0            UG    0         0        0   eth1


Initially I just had eth1 up and it worked fine to browse the internet and the local network. Yesterday I was given the Linksys router and I decided to play around with it by plugging an ethernet cable into one the LAN ports and my second NIC (eth0). I can connect fine to the Linksys router but can no longer connect to the internet or any computers on my local network (192.168.2.0) via eth1. If I disconnect the eth0 interface via NetworkManager or ifconfig then eth1 works fine again. Basically the message I get when I attempt to ping any computers on eth1's network is "ping: sendmsg: Operation not permitted" which leads me to believe it's some kind of routing problem.

I have also tried using DHCP to grab IP addresses and the result is the same. Using the NetworkManager connection editor I tried to limit eth0 by checking the box "use this connection only for resources on it's network" in the "routing" section. This appears to have no effect and doesn't appear to alter the routing table either from what I can tell.

Finally I just skipped using NetworkManager altogether and manually setup both NICs in the "/etc/network/interfaces" file. First I tried to do this with NetworkManager still enabled and when that didn't work I disabled NetworkManager completely but upon reboot I got the same result (no internet if eth0 is enabled and full internet access when eth0 is down).

I am totally stumped and wonder why something that's so trivial to do in either Windows or OS X is such a pain in Ubuntu. I don't recall having this kind of problem years back with a similar setup using either FreeBSD and RedHat so I am wondering if this is a problem specific to Ubuntu and/or NetworkManager. I am not too thrilled with the way NetworkManager handles either name resolution (rewriting "/etc/resolv.conf") or multiple NICs but the alternatives out there don't look a whole lot better (Connman, WICD, etc.)

Obviously I can just plug the Linksys router into my previously functioning local network (192.168.2.0) and not have this problem but I really bugs me that such a simple setup can't be made to work easily with the built-in GUI tools. Help!

---

