---
title: "Using one internet connection for server and sharing another (three interfaces)"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by krizze on 2009-10-11
Hi, I was wondering if it was possible to make a server use 1 IP for it's own internet connection, and forwarding/masquerading another.

My current setup:


Server:
eth0: connected to internet via cable (dhcp with wpa_supplicant (802.1X login))
eth1: connected to internal network via cable (192.168.11.2), running dhcp-server and sharing eth0's connection (masquerading)
eth2: currently not in use (planning to get another internet-ip via dhcp)

Network:
Some machines running on the 192.168.11.x network

Case:
As my ISP blocks certain ports, I use some of them on the server,
but would like the same ports forwarded to one of the pc's on the internal network. Naturally, this is not possible without getting another internet IP. My ISP allow multiple IP's as long as you authenticate with one interface first.

What I want is to use the eth0 connection only for the server, and connect another internet-cable to eth2 (giving me another internet-ip via dhcp).
I want eth2 to be shared (masquerade/nat) with the internal network (eth1).

How would I proceed with this in an /etc/network/interfaces file?

Connecting both eth0 and eth2 and requesting dhcp gives me two ip's, but also two default gw's, resulting in the server not getting a response from the internet. Probably not a big deal, but I'm pretty green on these things.

What I have now in /etc/network/interfaces:

#/etc/network/interfaces -- configuration file for ifup(8), ifdown(8)

# The loopback interface
# automatically added when upgrading

auto lo eth0 eth1
iface lo inet loopback

iface eth0 inet dhcp
pre-up wpa_supplicant -Dwired -ieth0 -c /etc/wpa_supplicant/wpa_supplicant.conf -B


iface eth1 inet static
        address 192.168.11.2
        netmask 255.255.255.0
        network 192.168.11.0
        broadcast 192.168.11.255

post-up echo 1 > /proc/sys/net/ipv4/ip_forward
post-up iptables -t nat -A POSTROUTING -s 192.168.11.0/24 -j MASQUERADE
post-up iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
post-up iptables -A FORWARD -o eth1 -i eth0 -j ACCEPT



Any help greatly appreciated :)

---

