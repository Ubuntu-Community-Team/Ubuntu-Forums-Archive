---
title: "DHCP - strange issues"
date: 2013-02-13
forum: Networking &amp; Wireless
---

### Post by R0peE on 2013-02-13
Hey everybody. At my company I have encountered a strange dhcp server issue. Actually there are 2 issues. The first one is, in one of my ip pools I use deny unknown-clients statement, but if I create a host without ip address, only mac address specifid, the dhcp server thinks that the client is unknown. I have plenty of free leases. The second problem is, that I would like to specify the domain names with the dhcp sever using ddns, but if I set ignore client-updates; they are not ignored and the client machines hostname is used, not the one I specified in the dhcp config.

This is my dhcp server configuration:

```
ddns-updates on;
ddns-update-style interim;
deny client-updates;
get-lease-hostnames true;
use-host-decl-names on;
default-lease-time 14400;
max-lease-time 14400;
update-static-leases on;
one-lease-per-client on;
authoritative;
log-facility local7;
include "/etc/bind/xxx.key";
shared-network "xxx" {
subnet 192.168.6.0 netmask 255.255.255.0 {
range 192.168.6.70 192.168.6.100;
deny unknown-clients;
zone 6.168.192.in-addr.arpa. { primary 127.0.0.1; key xxx-key; }
zone xxx. { primary 127.0.0.1; key xxx-key; }
option domain-name "xxx";
option domain-name-servers 192.168.6.254;
option routers 192.168.6.254;
option netbios-node-type 8;
option subnet-mask 255.255.255.0;
}
subnet 192.168.10.0 netmask 255.255.255.0 {
range 192.168.10.10 192.168.10.110;
allow unknown-clients;
zone 10.168.192.in-addr.arpa. { primary 127.0.0.1; key xxx-key; }
zone vendeg.xxx. { primary 127.0.0.1; key xxx-key; }
ignore client-updates;
option routers 192.168.10.254;
option subnet-mask 255.255.255.0;
option domain-name-servers 192.168.10.254;
option domain-name "vendeg.xxx";
option netbios-node-type 8;
}
}
```

And this is what I see in the logs:

```
Feb 8 13:47:23 dhcpd: DHCPDISCOVER from 74:2f:xx:xx:xx:xx via eth1
Feb 8 13:47:24 dhcpd: DHCPOFFER on 192.168.10.20 to 74:2f:xx:xx:xx:xx (xxx) via eth1
Feb 8 13:47:24 dhcpd: Added new forward map from xxx to 192.168.10.20
Feb 8 13:47:24 dhcpd: added reverse map from 20.10.168.192.in-addr.arpa. to xxx
Feb 8 13:47:24 dhcpd: DHCPREQUEST for 192.168.10.20 (192.168.6.254) from 74:2f:xx:xx:xx:xx (xxx) via eth1
Feb 8 13:47:24 dhcpd: DHCPACK on 192.168.10.20 to 74:2f:xx:xx:xx:xx (xxx) via eth1
Feb 8 13:50:05 dhcpd: DHCPREQUEST for 192.168.10.20 from 74:2f:xx:xx:xx:xx (xxx) via eth1
Feb 8 13:50:05 dhcpd: DHCPACK on 192.168.10.20 to 74:2f:xx:xx:xx:xx (xxx) via eth1
```

Oh and I use LDAP to store the dhcp config, and the host configuration looks like this in the LDAP tree:

```
dn: cn=xxx.wifi,cn=192.168.6.0,cn=xxx,cn=dhcp,dc=ldap,dc=xxx
cn: xxx.wifi
dhcphwaddress: ethernet 74:2f:xx:xx:xx:xx
dhcpoption: host-name "xxx.wifi"
objectclass: top
objectclass: dhcpHost
```

I would realy appreciate some help, this problem is starting to get realy annoying because there is no error or warning or something to get started on. Thank you!!

---

### Post by schragge on 2013-02-13
About the second issue. To be honest, I don't see anything wrong here. If *ingnore client-updates* is used then dhcp server first tries to set the hostname from *ddns-hostname*. Since there is no such option, it constructs the FQDN as the hostname sent by client plus its own domainname. Correct me if I'm wrong.

---

### Post by R0peE on 2013-02-13
I see, but I have the use-host-decl-names on; statement and it should define that the hostname comes from the host definition, not from the ddns-hostname

---

### Post by schragge on 2013-02-13
You're right, but there's no explicit *host* declaration either.
[COLOR=blue]**Edit.**[/COLOR]
Oh I see, it's being retrieved from LDAP. Just guessing, shouldn't the dhcpd.conf say *ldap-method dynamic;* in this case?

---

### Post by R0peE on 2013-02-14
bump

---

