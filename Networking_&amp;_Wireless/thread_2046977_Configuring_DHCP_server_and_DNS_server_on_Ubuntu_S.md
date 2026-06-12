---
title: "Configuring DHCP server and DNS server on Ubuntu Server 12.04"
date: 2012-08-23
forum: Networking &amp; Wireless
---

### Post by agarod on 2012-08-23
SOLVED

Last 4 lines of /etc/bind/zones/admsr.com.db are now:

@ IN         NS         ns.admsr.com.
ns IN A 192.168.2.101
gw                IN         A            192.168.2.2
                    TXT         "Network Gateway"

-------------------------------------------

My first post here.

         Relevant info:

  Host OS: Windows 7 Home Premium 64-bits with VMware Workstation 8
  Two VMs: Ubuntu Server 12.04 and Ubuntu Desktop 12.04

  VMware NAT settings:
  Use local DHCP service is DISABLED
  Subnet IP: 192.168.2.0
  Subnet mask: 255.255.255.0
  Gateway IP: 192.168.2.2

  On Ubuntu Server I have a DHCP server: isc-dhcp-server
  DHCP is working OK. IPs range: 192.168.2.201 - 192.168.2.210

  On Ubuntu Server I have a DNS server: bind9

  /etc/network/interfaces

      auto eth0     iface eth0 inet static
address 192.168.2.101
netmask 255.255.255.0
gateway 192.168.2.2

/etc/bind/named.conf.local

      zone "admsr.com" {
type master;
file "/etc/bind/zones/admsr.com.db";
};

zone "2.168.192.in-addr.arpa" {
type master;
file "/etc/bind/zones/rev.2.168.192.in-addr.arpa";
};

/etc/bind/named.conf.options

      forwarders {
8.8.8.8;
8.8.4.4;
};

/etc/resolv.conf

      search admsr.com.
nameserver 192.168.2.101

/etc/bind/zones/admsr.com.db

      $TTL 3D
@ IN       SOA    ns.admsr.com. admin.admsr.com. (
          2007062001
          28800
          3600
          604800
          38400
);
admsr.com.  IN         NS         ns.admsr.com.
gw                IN         A            192.168.2.2
                    TXT         "Network Gateway"

/etc/bind/zones/rev.2.168.192.in-addr.arpa

      $TTL 3D     @       IN         SOA         ns.admsr.com. admin.admsr.com. (
                         2007062001
                         28800
                         604800
                         604800
                         86400
)
             IN         NS          ns.admsr.com.
2                 IN         PTR        gw.admsr.com.

Now, with: dig admsr.com the status is SERVFAIL
  
And with: nslookup gw I get:

      Server:     192.168.2.101
Address:    192.168.2.101#53
Non-authoritative answer:
*** Can't find gw: No answer

Both VMs: Ubuntu Server and Ubuntu Desktop are using NAT for network connection in VMware.

  Ubuntu Desktop Network Settings are:

      IP Address: 192.168.2.201 <- assigned by DHCP server on Ubuntu Server     Subnet Mask: 255.255.255.0
Default Route: 192.168.2.2
DNS: 8.8.8.8 8.8.4.4

When DNS works OK I will change the line in /etc/dhcp/dhcpd.conf

      option domain-name-servers 8.8.8.8, 8.8.4.4;

for

      option domain-name-servers 192.168.2.101;

TIA

Edit:
Problem fixed with the Ubuntu Desktop VM. Can access Internet now.

Changed in /etc/dhcp/dhcpd.conf the line:

option routers 192.168.2.1;

for:

option routers 192.3168.2.2;

---

