---
title: "Dynamic DNS"
date: 2012-03-20
forum: Networking &amp; Wireless
---

### Post by nethompson on 2012-03-20
[SIZE=3]I have been trying to setup a DDNS server with no luck. I feel like I am almost there but when I restart the bind service and get the DHCP lease from the server I get a couple of errors. The first error is with the journal file stating that "journal rollforward failed: no more". I have Googled this with no luck. The error that comes directly after the first error is that the zone is not loaded due to errors which doesn't tell me much. I'm assuming the second error has something to do with the first. Here are my dhcp and bind configuration and zone files. Any help would be greatly appreciated![/SIZE]
 
[SIZE=3]reverse dns zone:[/SIZE]
 
[FONT=Courier New][FONT=Verdana][SIZE=3]$ORIGIN 62.209.160.IN-ADDR.ARPA.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]$TTL 604800[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]@ IN SOA test.com. root.test.com ([/SIZE][/FONT]
[FONT=Courier New][SIZE=3]1011 ; Serial[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]604800 ; Refresh[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]86400 ; Retry[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]2419200 ; Expire[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]604800 ) ; Negative Cache TTL[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]IN NS MIDC-2UA00302DB.test.com.[/SIZE][/FONT]
[/FONT]
 
[FONT=Courier New][FONT=Verdana][SIZE=3]primary dns zone:[/SIZE][/FONT][/FONT]
 
[FONT=Courier New][FONT=Courier New][FONT=Verdana][SIZE=3]$ORIGIN test.com.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]$TTL 604800[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]@ IN SOA test.com. root.test.com ([/SIZE][/FONT]
[FONT=Courier New][SIZE=3]1011 ; Serial[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]604800 ; Refresh[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]86400 ; Retry[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]2419200 ; Expire[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]604800 ) ; Negative Cache TTL[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]IN NS MIDC-2UA00302DB[/SIZE][/FONT]
 
 
[/FONT]
[FONT=Courier New][FONT=Verdana][SIZE=3]named config file:[/SIZE][/FONT][/FONT]
 
[FONT=Courier New][FONT=Courier New][FONT=Verdana][SIZE=3]// This is the primary configuration file for the BIND DNS server named.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]//[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]// Please read /usr/share/doc/bind9/README.Debian.gz for information on the [/SIZE][/FONT]
[FONT=Courier New][SIZE=3]// structure of BIND configuration files in Debian, *BEFORE* you customize [/SIZE][/FONT]
[FONT=Courier New][SIZE=3]// this configuration file.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]//[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]// If you are just adding zones, please do that in /etc/bind/named.conf.local[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]include "/etc/bind/named.conf.options";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]include "/etc/bind/named.conf.local";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]include "/etc/bind/named.conf.default-zones";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]include "/etc/bind/rndc.key";[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]controls {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]inet 127.0.0.1 port 953 allow { 127.0.0.1; } keys { rndc-key; };[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]};[/SIZE][/FONT]
 
 
[FONT=Courier New][SIZE=3]zone "test.com" {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]type master;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]file "/etc/bind/db.test";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]allow-query{any;};[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]allow-update {localhost;};[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]notify no;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]};[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]zone "62.209.160.in-addr.arpa" IN {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]type master;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]file "/etc/bind/db.rev.test";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]allow-query{any;};[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]allow-update {localhost;};[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]notify no;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]};[/SIZE][/FONT]
[/FONT]
 
 
 
[FONT=Courier New][FONT=Verdana][SIZE=3]dhcpd config file:[/SIZE][/FONT][/FONT]
 
[FONT=Courier New][SIZE=3]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# Sample configuration file for ISC dhcpd for Debian[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# configuration file instead of this file.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# The ddns-updates-style parameter controls whether or not the server will[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# attempt to do a DNS update when a lease is confirmed. We default to the[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# behavior of the version 2 packages ('none', since DHCP v2 didn't[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# have support for DDNS.)[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]deny client-updates;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]allow unknown-clients;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#ignore unknown-clients;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]update-static-leases on;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]ddns-domainname "test.com";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]ddns-rev-domainname "62.209.160.in-addr.arpa";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]ddns-update-style interim;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]ddns-updates on;[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# option definitions common to all supported networks...[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]option domain-name "test.com";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]option domain-name-servers 160.209.62.186;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]option netbios-name-servers 160.209.62.186;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]option routers 160.209.62.1;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]default-lease-time 86400;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]max-lease-time 172800;[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# If this DHCP server is the official DHCP server for the local[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# network, the authoritative directive should be uncommented.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]authoritative;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]one-lease-per-client on;[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# Use this to send dhcp log messages to a different log file (you also[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# have to hack syslog.conf to complete the redirection).[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]log-facility local7;[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# No service will be given on this subnet, but declaring it helps the [/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# DHCP server to understand the network topology.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]#subnet 10.152.187.0 netmask 255.255.255.0 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# This is a very basic subnet declaration.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]#subnet 10.254.239.0 netmask 255.255.255.224 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# range 10.254.239.10 10.254.239.20;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# This declaration allows BOOTP clients to get dynamic addresses,[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# which we don't really recommend.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]#subnet 10.254.239.32 netmask 255.255.255.224 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# range dynamic-bootp 10.254.239.40 10.254.239.60;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option broadcast-address 10.254.239.31;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option routers rtr-239-32-1.example.org;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]include "/etc/dhcp3/rndc.key";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]zone test.com. {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]primary 160.209.62.186;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]key "rndc-key";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]zone 62.209.160.in-addr.arpa. {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]primary 160.209.62.186;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]key "rndc-key";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# A slightly different configuration for an internal subnet.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]subnet 160.209.62.0 netmask 255.255.255.0 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]range 160.209.62.200 160.209.62.250;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]option domain-name-servers 160.209.62.186;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]option domain-name "test.com";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option routers 160.209.62.1;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option broadcast-address 10.5.5.31;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]default-lease-time 86400;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]max-lease-time 172800;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# Hosts which require special configuration options can be listed in[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# host statements. If no address is specified, the address will be[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# allocated dynamically (if possible), but the host-specific information[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# will still come from the host declaration.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]#host passacaglia {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# hardware ethernet 0:0:c0:5d:bd:95;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# filename "vmunix.passacaglia";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# server-name "toccata.fugue.com";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# Fixed IP addresses can also be specified for hosts. These addresses[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# should not also be listed as being available for dynamic assignment.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# Hosts for which fixed IP addresses have been specified can boot using[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# BOOTP or DHCP. Hosts for which no fixed address is specified can only[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# be booted with DHCP, unless there is an address range on the subnet[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# to which a BOOTP client is connected which has the dynamic-bootp flag[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# set.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#host fantasia {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# hardware ethernet 08:00:07:26:c0:a5;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# fixed-address fantasia.fugue.com;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# You can declare a class of clients and then do address allocation[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# based on that. The example below shows a case where all clients[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# in a certain class get addresses on the 10.17.224/24 subnet, and all[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# other clients get addresses on the 10.0.29/24 subnet.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]#class "foo" {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# match if substring (option vendor-class-identifier, 0, 4) = "SUNW";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]#shared-network 224-29 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# subnet 10.17.224.0 netmask 255.255.255.0 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option routers rtr-224.example.org;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# }[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# subnet 10.0.29.0 netmask 255.255.255.0 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option routers rtr-29.example.org;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# }[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# pool {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# allow members of "foo";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# range 10.17.224.10 10.17.224.250;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# }[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# pool {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# deny members of "foo";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# range 10.0.29.10 10.0.29.230;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# }[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
[SIZE=3][/SIZE] 
[SIZE=3][/SIZE] 
[SIZE=3][/SIZE] 
[SIZE=3][/SIZE] 
[SIZE=3]I was finally able to remove the journal error message by deleting the file but dhcp is still not updating the dns records. [/SIZE][/FONT][/FONT]

---

### Post by nethompson on 2012-03-22
> **nethompson said:**
> [SIZE=3]I have been trying to setup a DDNS server with no luck. I feel like I am almost there but when I restart the bind service and get the DHCP lease from the server I get a couple of errors. The first error is with the journal file stating that "journal rollforward failed: no more". I have Googled this with no luck. The error that comes directly after the first error is that the zone is not loaded due to errors which doesn't tell me much. I'm assuming the second error has something to do with the first. Here are my dhcp and bind configuration and zone files. Any help would be greatly appreciated![/SIZE]
 
[SIZE=3]reverse dns zone:[/SIZE]
 
[FONT=Courier New][FONT=Verdana][SIZE=3]$ORIGIN 62.209.160.IN-ADDR.ARPA.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]$TTL 604800[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]@ IN SOA test.com. root.test.com ([/SIZE][/FONT]
[FONT=Courier New][SIZE=3]1011 ; Serial[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]604800 ; Refresh[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]86400 ; Retry[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]2419200 ; Expire[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]604800 ) ; Negative Cache TTL[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]IN NS MIDC-2UA00302DB.test.com.[/SIZE][/FONT]
[/FONT]
 
[FONT=Courier New][FONT=Verdana][SIZE=3]primary dns zone:[/SIZE][/FONT][/FONT]
 
[FONT=Courier New][FONT=Courier New][FONT=Verdana][SIZE=3]$ORIGIN test.com.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]$TTL 604800[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]@ IN SOA test.com. root.test.com ([/SIZE][/FONT]
[FONT=Courier New][SIZE=3]1011 ; Serial[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]604800 ; Refresh[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]86400 ; Retry[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]2419200 ; Expire[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]604800 ) ; Negative Cache TTL[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]IN NS MIDC-2UA00302DB[/SIZE][/FONT]
 
 
[/FONT]
[FONT=Courier New][FONT=Verdana][SIZE=3]named config file:[/SIZE][/FONT][/FONT]
 
[FONT=Courier New][FONT=Courier New][FONT=Verdana][SIZE=3]// This is the primary configuration file for the BIND DNS server named.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]//[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]// Please read /usr/share/doc/bind9/README.Debian.gz for information on the [/SIZE][/FONT]
[FONT=Courier New][SIZE=3]// structure of BIND configuration files in Debian, *BEFORE* you customize [/SIZE][/FONT]
[FONT=Courier New][SIZE=3]// this configuration file.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]//[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]// If you are just adding zones, please do that in /etc/bind/named.conf.local[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]include "/etc/bind/named.conf.options";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]include "/etc/bind/named.conf.local";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]include "/etc/bind/named.conf.default-zones";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]include "/etc/bind/rndc.key";[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]controls {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]inet 127.0.0.1 port 953 allow { 127.0.0.1; } keys { rndc-key; };[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]};[/SIZE][/FONT]
 
 
[FONT=Courier New][SIZE=3]zone "test.com" {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]type master;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]file "/etc/bind/db.test";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]allow-query{any;};[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]allow-update {localhost;};[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]notify no;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]};[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]zone "62.209.160.in-addr.arpa" IN {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]type master;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]file "/etc/bind/db.rev.test";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]allow-query{any;};[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]allow-update {localhost;};[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]notify no;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]};[/SIZE][/FONT]
[/FONT]
 
 
 
[FONT=Courier New][FONT=Verdana][SIZE=3]dhcpd config file:[/SIZE][/FONT][/FONT]
 
[FONT=Courier New][SIZE=3]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# Sample configuration file for ISC dhcpd for Debian[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# configuration file instead of this file.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# The ddns-updates-style parameter controls whether or not the server will[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# attempt to do a DNS update when a lease is confirmed. We default to the[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# behavior of the version 2 packages ('none', since DHCP v2 didn't[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# have support for DDNS.)[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]deny client-updates;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]allow unknown-clients;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#ignore unknown-clients;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]update-static-leases on;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]ddns-domainname "test.com";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]ddns-rev-domainname "62.209.160.in-addr.arpa";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]ddns-update-style interim;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]ddns-updates on;[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# option definitions common to all supported networks...[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]option domain-name "test.com";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]option domain-name-servers 160.209.62.186;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]option netbios-name-servers 160.209.62.186;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]option routers 160.209.62.1;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]default-lease-time 86400;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]max-lease-time 172800;[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# If this DHCP server is the official DHCP server for the local[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# network, the authoritative directive should be uncommented.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]authoritative;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]one-lease-per-client on;[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# Use this to send dhcp log messages to a different log file (you also[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# have to hack syslog.conf to complete the redirection).[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]log-facility local7;[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# No service will be given on this subnet, but declaring it helps the [/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# DHCP server to understand the network topology.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]#subnet 10.152.187.0 netmask 255.255.255.0 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# This is a very basic subnet declaration.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]#subnet 10.254.239.0 netmask 255.255.255.224 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# range 10.254.239.10 10.254.239.20;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# This declaration allows BOOTP clients to get dynamic addresses,[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# which we don't really recommend.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]#subnet 10.254.239.32 netmask 255.255.255.224 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# range dynamic-bootp 10.254.239.40 10.254.239.60;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option broadcast-address 10.254.239.31;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option routers rtr-239-32-1.example.org;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]include "/etc/dhcp3/rndc.key";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]zone test.com. {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]primary 160.209.62.186;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]key "rndc-key";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]zone 62.209.160.in-addr.arpa. {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]primary 160.209.62.186;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]key "rndc-key";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# A slightly different configuration for an internal subnet.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]subnet 160.209.62.0 netmask 255.255.255.0 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]range 160.209.62.200 160.209.62.250;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]option domain-name-servers 160.209.62.186;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]option domain-name "test.com";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option routers 160.209.62.1;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option broadcast-address 10.5.5.31;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]default-lease-time 86400;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]max-lease-time 172800;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# Hosts which require special configuration options can be listed in[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# host statements. If no address is specified, the address will be[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# allocated dynamically (if possible), but the host-specific information[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# will still come from the host declaration.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]#host passacaglia {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# hardware ethernet 0:0:c0:5d:bd:95;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# filename "vmunix.passacaglia";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# server-name "toccata.fugue.com";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# Fixed IP addresses can also be specified for hosts. These addresses[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# should not also be listed as being available for dynamic assignment.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# Hosts for which fixed IP addresses have been specified can boot using[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# BOOTP or DHCP. Hosts for which no fixed address is specified can only[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# be booted with DHCP, unless there is an address range on the subnet[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# to which a BOOTP client is connected which has the dynamic-bootp flag[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# set.[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#host fantasia {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# hardware ethernet 08:00:07:26:c0:a5;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# fixed-address fantasia.fugue.com;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]# You can declare a class of clients and then do address allocation[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# based on that. The example below shows a case where all clients[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# in a certain class get addresses on the 10.17.224/24 subnet, and all[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# other clients get addresses on the 10.0.29/24 subnet.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]#class "foo" {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# match if substring (option vendor-class-identifier, 0, 4) = "SUNW";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=3]#shared-network 224-29 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# subnet 10.17.224.0 netmask 255.255.255.0 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option routers rtr-224.example.org;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# }[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# subnet 10.0.29.0 netmask 255.255.255.0 {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# option routers rtr-29.example.org;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# }[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# pool {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# allow members of "foo";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# range 10.17.224.10 10.17.224.250;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# }[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# pool {[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# deny members of "foo";[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# range 10.0.29.10 10.0.29.230;[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]# }[/SIZE][/FONT]
[FONT=Courier New][SIZE=3]#}[/SIZE][/FONT]
 
 
 
 
[SIZE=3]I was finally able to remove the journal error message by deleting the file but dhcp is still not updating the dns records. [/SIZE][/FONT][/FONT]


No help on this...?

---

