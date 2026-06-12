---
title: "resolv.conf: multiple nameserver entries"
date: 2009-10-16
forum: Networking &amp; Wireless
---

### Post by crypticlabs on 2009-10-16
Setup: Ubuntu 9.10 Beta.

My laptop receives it's network information via DHCP using NetworkManager from a router. In particular, it receives one DNS server to query and a search entry for host-name lookups.

Example:

nameserver 1.1.1.1
search home.com

When I connect to a remote network using NetworkManager-vpnc, it receives 2 DNS servers to query and a search entry for host-name lookups. These are added to the resolv.conf file, on top of the existing entries.

Example:

nameserver 2.2.2.2
nameserver 3.3.3.3
nameserver 1.1.1.1
search remotenetwork.com home.com

Because of this order, all of my DNS queris are done against 2.2.2.2. I only want to use the VPN's DNS servers for hostnames on that VPN network that my DNS server (1.1.1.1) doesn't have.

I have no problem switching the order of the list of nameservers as well as the search order using the NetworkManager so that resolv.conf reflects:

Example:

nameserver 1.1.1.1
nameserver 2.2.2.2
nameserver 3.3.3.3
search home.com remotenetwork.com

The problem or issue that I am having is  when I have it set like this, my resolver isn't going through the list as defined in the resolver man page. It will only query the first DNS server and not the rest. I know that the query works because given my last example, if I want to ping host1.remotenetwork.com, it doesn't work, but if I issue the command dig @2.2.2.2 host1.remotenetwork.com, I see that my laptop can query the VPN DNS server and properly resolve that name

I'm not sure if this is an issue with the resolver or if it is with NetworkManager or with NetworkManager-vpnc.

I've also tried editing the /etc/resolvconf/interface-order so that my eth* is polled before the tun* interface (as tun* was listed before eth*), similar to the bind order in Windows, but I that didn't work.

Any help would be greatly appreciated.

---

