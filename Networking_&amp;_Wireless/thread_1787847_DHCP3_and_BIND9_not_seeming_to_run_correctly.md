---
title: "DHCP3 and BIND9 not seeming to run correctly"
date: 2011-06-21
forum: Networking &amp; Wireless
---

### Post by danieljay on 2011-06-21
I have been trying to learn how to run a linux box as a router for my home. I have removed my WRT54GL router with DD-WRT from the network and made a linux firewall box. The box runs a VPN server, DHCP3, BIND9 and a few other things. The machine is a VM running on ESXi and has 2 nics assigned to it. The eth0 is the Internet and eth1 is the local safe network. I am noticing that DHCP is not updating my BIND9 zone files with the A records. I will post my config files. What might be wrong with my setup?

/etc/dhcpd3/dhcpd.conf
```
key "rndc-key" {
        algorithm hmac-md5;
        secret "key here";
};

ddns-update-style interim;
ddns-domainname "thehouse.lan";
ddns-rev-domainname "90.10.10.in-addr.arpa";

option domain-name "thehouse.lan";
option domain-name-servers 10.10.90.2;

default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

zone thehouse.lan. {
primary 127.0.0.1;
key "rndc-key";
}

# Safe network
subnet 10.10.90.0 netmask 255.255.255.0 {
        option domain-name-servers 10.10.90.2;
        option broadcast-address 10.10.90.255;
        option subnet-mask 255.255.255.0;
        option routers 10.10.90.2;
        range 10.10.90.50 10.10.90.60;
        zone 10.10.90.in-addr.arpa. {
                primary 10.10.90.2;
                key "rndc-key";
                }
        }


```
/etc/bind/named.conf.options
```
options {
	directory "/var/cache/bind";

	forwarders {
		208.67.222.222;
		208.67.220.220;
		};

	recursion yes;
	version "REFUSED";

	allow-recursion {
		127.0.0.1;
		10.10.90.0/24;
	};

	allow-query {
		127.0.0.1;
		10.10.90.0/24;
	};

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};
```
/etc/bind/named.conf.local
```
include "/etc/bind/rndc.key";

zone "thehouse.lan" {
        type master;
        file "/etc/bind/zones/thehouse.lan.db";
	allow-update { key "rndc-key"; };
        };

zone "90.10.10.in-addr.arpa" {
     type master;
     notify no;
     file "/etc/bind/zones/rev.90.10.10.in-addr.arpa";
     allow-update { key "rndc-key"; };
};
```
/etc/bind/zones/rev.90.10.10.in-addr.arpa
```
$ORIGIN .
$TTL 86400      ; 1 day
90.10.10.in-addr.arpa	IN	SOA	thehouse.lan. me.gmail.com. (
			200806302
			28800
			7200
			2419200
			86400 )
                       NS      ns.thehouse.lan.
$ORIGIN 90.10.10.in-addr.arpa.
$TTL 86400      ; 1 day
2                       PTR     network.thehouse.lan.
12                    	PTR     www1.thehouse.lan.
```
/etc/bind/zones/thehouse.lan.db
```
$ORIGIN .
$TTL 86400	; 1 day
thehouse.lan	IN	SOA	ns.thehouse.lan. me.gmail.com. (
			200806368
			28800
			7200
			2419200
			86400 )
			NS	ns.thehouse.lan.
			A	10.10.90.2
$ORIGIN thehouse.lan.
$TTL 86400	; 1 day
ns			A	10.10.90.2
www1			A	10.10.90.12
```

The /etc/resolv.conf on one of the local machines
```
domain thehouse.lan
search thehouse.lan
nameserver 10.10.90.2
```
Any help would be great.

---

### Post by danieljay on 2011-06-26
Anybody have a suggestion for this one?

---

