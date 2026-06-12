---
title: "NetworkManager DHCPv6"
date: 2011-02-15
forum: Networking &amp; Wireless
---

### Post by jcornwall on 2011-02-15
NetworkManager 0.8.1, which comes with Ubuntu 10.10, claims to support the DHCPv6 protocol. However, I can't for the life of me make it work.

I have an Ubuntu server running radvd (AdvAutonomous off, AdvManaged on) and dibbler-server. Running dibbler-client on the client Ubuntu system correctly obtains an IP and other details from the server. Windows 7, without the Dibbler client, also successfully autoconfigures by sending DHCP6 packets and obtaining an address from the DHCP server.

However, I'd rather use NetworkManager on Ubuntu. I have selected Automatic configuration for IPv6 and it does indeed make an attempt to configure IPv6 connectivity. With 'AdvAutonomous on' in radvd, NetworkManager successfully assigns itself an IP. But with 'AdvAutonomous off' on the server, it makes no attempt to send out DHCP6 packets instead. It actually does very little except determine that autonomous IP configuration is configured off at the route advertisement daemon.

Does DHCPv6 work for anyone in NetworkManager, or is it just broken?

---

### Post by CloneSan on 2011-04-03
Can't seem to get networkmanager in ubuntu 10.10 with dhcp6 to work as well (and kubuntu doesn't have any ipv6 options at all in seems).

Little question for you though: you are using dibbler-client, does it start succesfully at boot? Here it is trying to use the ipv6 link local address at S20 when it hasn't been configured yet (kubuntu 10.10).

2011.04.02 21:31:22 Client Critical  Interface eth0/2 is down or doesn't have any link-local address.
2011.04.02 21:31:22 Client Critical  Fatal error during CfgMgr initialization.

My simple dibbler client config:

log-level 8
iface eth0 {
ia
}

eth0 is configured via networkmanager (dhcp). Just curious if I am the only one with that particular problem.

In any case, this link: [https://wiki.kubuntu.org/DHCPv6](https://wiki.kubuntu.org/DHCPv6) shows that ubuntu
11 has moved (probably for good reason) to isc-dhcp, which I am using on centos with success (using a self build fedora 11 rpm).

PS.

The developer of dibbler is also again actively developing the dhcp6 server/client

---

### Post by cprofitt on 2011-04-18
I am curious if any headway was ever made with this. I am trying to get my systems to work with IPv6 currently as I finally got a router that supports IPv6.

---

