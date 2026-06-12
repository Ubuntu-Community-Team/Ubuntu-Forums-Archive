---
title: "Setting up two network interfaces (dhcp &amp; static)"
date: 2013-06-28
forum: Networking &amp; Wireless
---

### Post by onebasilikum on 2013-06-28
I'm working in Ubuntu 12.04 and I'm trying to set up a server with two network interfaces. One interface (eth0) uses dhcp and the other one (eth1) has a static ip. The problem is that if both interfaces are up, I cannot resolve names that are in the eth1-network. If I put down eth0, than it works fine.

Here is my /etc/network/interfaces:

```
auto lo
iface lo inet loopback

auto eth0 eth1

iface eth0 inet dhcp

iface eth1 inet static
      address 192.168.0.101
      netmask 255.255.255.0
      # broadcast 192.168.0.255
      # gateway 192.168.0.1
      # dns-* options are implemented by the resolvconf package, if installed
      dns-nameservers 192.168.0.1
      dns-search example.test.org
      dns-domain example.test.org
```

I have comment out broadcast and gateway, otherwise eth1 won't even come up. After that configuration, my /etc/resolv.conf looks like this:

```
nameserver x.x.x.90
nameserver x.x.x.91
nameserver 192.168.0.1
search example.test.org

```

So the first two addresses are provided via dhcp and the last one is the one that I provided in my /etc/network/interfaces file. Now lets say I have an host called "ihost12" with the ip address 192.168.0.12. I can connect to the ip address via ssh, no problem. But if I try to connect to it via name, or if I try to resolve the hostname with the "host" command, it won't find it. 
But if I take down eth0, my /etc/resolv.conf changes to this:

```
nameserver 192.168.0.1
search example.test.org

```

and "ihost12" can also be resolved. So I was wondering, does the order in which the nameservers are defined in resolv.conf matter? And what can I check or try to solve this problem?

---

### Post by jdthood on 2013-06-28
Yes, the order in which nameserver addresses are listed in resolv.conf matters. The glibc resolver tries the addresses in the listed order until it receives an answer.

This explains why you cannot resolve the name "ihost12" on 192.168.0/24 when eth0 is up. Then nameserver x.x.x.90 is consulted and it answers that there is no such domain name in Internet DNS.

What you need to do is arrange for the eth1-related nameserver address to have a higher priority than the eth0-related nameserver address. The way to arrange for this (assuming you are using resolvconf, which is the default in Ubuntu 12.04 and later... make sure that /etc/resolv.conf is a symbolic link to "../run/resolvconf/resolv.conf") is to edit /etc/resolvconf/interface-order. If you have version 1.69ubuntu1 of resolvconf then put a line "eth1*" just above the line "eth*" in that file.

Minor issue: You don't need the "dns-domain" option in /etc/network/interfaces. It is entirely redundant and deprecated.

---

### Post by onebasilikum on 2013-06-28
Brilliant! Thanks a lot, that solved it :) And I removed the line "dns-domain" again. That was one of the things that I just blindly tried out but obviously had no effect on my issue.

---

### Post by PyPF3XL on 2013-09-03
> **jdthood said:**
> Yes, the order in which nameserver addresses are listed in resolv.conf matters. The glibc resolver tries the addresses in the listed order until it receives an answer.

This explains why you cannot resolve the name "ihost12" on 192.168.0/24 when eth0 is up. Then nameserver x.x.x.90 is consulted and it answers that there is no such domain name in Internet DNS.

What you need to do is arrange for the eth1-related nameserver address to have a higher priority than the eth0-related nameserver address. The way to arrange for this (assuming you are using resolvconf, which is the default in Ubuntu 12.04 and later... make sure that /etc/resolv.conf is a symbolic link to "../run/resolvconf/resolv.conf") is to edit /etc/resolvconf/interface-order. If you have version 1.69ubuntu1 of resolvconf then put a line "eth1*" just above the line "eth*" in that file.

Minor issue: You don't need the "dns-domain" option in /etc/network/interfaces. It is entirely redundant and deprecated.


I have a similar issue where I am trying to set up a FOG server with 2 NIC interfaces (First interface, eth0 - Static and the second interface eth1 - DHCP). The reason I need to set it up this way is for security and performance reasons. The static interface (eth0) is to give me the ability to manage the system via http through any web browser. The second interface (eth1) is what I would like to set up to an 8 port switch that will just deploy images through PXE booting.

I have the server configured as a DHCP server but I can't seem to get machines to boot through PXE when connected on the second interface. Before segmenting the network I verified that this server works and that it can deploy images through PXE booting. But I feel that I have missed something in the DHCP configuration. I also thought of changing the IP route tables to see if that would make a difference but I haven't got to that point yet. Any help or advice on this would be greatly appreciated.

---

### Post by PyPF3XL on 2013-09-04
Found the solution to this. I basically had the "next server" address and DHCP wrong. Once configured correctly everything worked just fine. For future reference if you are looking to set up two separate interfaces (one for DHCP and the other as static to have two separate subnets) then make sure your "next server" lines up with the same address as the static IP you gave the DHCP interface.

For example, my eth0 (web interface) can be 192.168.1.1 and my eth1 (DHCP interface) is 1.1.1.1. Therefore I would want to make sure my "next server" address matches the same IP (1.1.1.1) as the DHCP interface.

---

