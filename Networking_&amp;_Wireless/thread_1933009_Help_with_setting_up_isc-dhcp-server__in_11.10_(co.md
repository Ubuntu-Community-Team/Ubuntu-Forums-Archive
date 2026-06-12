---
title: "Help with setting up isc-dhcp-server  in 11.10 (config file issues)"
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by miamitj on 2012-02-28
I'm kinda new to ubuntu and decided I was going to use 11.10 as a DHCP server for a school wide wireless I'm setting up.  We outgrew out old DHCP server and have roughly 1500 users on at this time.  I've configured the dhcpd.conf file as noted below but when users get assigned past the first 244 ip's I get "no available ip address" errors from the dhcp server.  I obviously have it configured wrong because its not automatically going to the next available range.

Ideas???  Thanks in advance ...

contents of dhcpd.conf:
__________________________________________________

# /etc/dhcp3/dhcpd.conf
#
#
ddns-update-style none;

# Lease time is in seconds
# Default lease is 1 week (604800 seconds)
default-lease-time 28800;
# Max lease is 4 weeks (2419200 seconds)
max-lease-time 28800;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
authoritative;

# All ip addresses and domain name are examples
subnet 172.16.0.0 netmask 255.255.248.0 {
    option domain-name "stbhswireless.org";
#   option broadcast-address 192.168.0.255;
    option subnet-mask 255.255.248.0;
    option domain-name-servers 172.16.0.2; # Comma between domain
    option routers 172.16.0.2;
    range 172.16.0.10 172.16.0.254;
    range 172.16.1.1 172.16.1.254;
    range 172.16.2.1 172.16.2.254;
    range 172.16.3.1 172.16.3.254;
    range 172.16.4.1 172.16.4.254;
    range 172.16.5.1 172.16.5.254;
    range 172.16.6.1 172.16.6.254;
    range 172.16.7.1 172.16.7.254;

}
__________________________________________________

---

### Post by miamitj on 2012-03-01
Anyone?

---

### Post by Ankit Mathur on 2012-06-21
I have a solution with little bit confusion. It would be very well if you please let me know the content of interfaces file and isc-dhcp-server file.

---

