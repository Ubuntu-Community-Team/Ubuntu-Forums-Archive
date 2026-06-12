---
title: "Issue with Bind, RARP working but not arp"
date: 2013-02-06
forum: Networking &amp; Wireless
---

### Post by grahambo2005 on 2013-02-06
Hi All

I'm having and issue with Bind

I want to set up the following in DNS:
```
Name:   server005.gbrac.ie
Address: 192.168.57.11
Name:   server005.gbrac.ie
Address: 192.168.57.12
Name:   server005.gbrac.ie
Address: 192.168.57.13

Name:   server005n0-vip.gbrac.ie
Address: 192.168.57.106

Name:   server005n1-vip.gbrac.ie
Address: 192.168.57.107

Name:   server005n0.gbrac.ie
Address: 192.168.56.106

Name:   server005n1.gbrac.ie
Address: 192.168.56.107
```

I've done so in bind and Reverse reverse translation is working:

```
root@DNSServer:/etc/bind# nslookup 192.168.56.106
Server:         192.168.56.199
Address:        192.168.56.199#53

106.56.168.192.in-addr.arpa     name = server005n0.gbrac.ie.56.168.192.in-addr.arpa.

```

However when I lookup the server name I get nothing:

```
root@DNSServer:/etc/bind# nslookup server005n0.gbrac.ie
Server:         192.168.56.199
Address:        192.168.56.199#53

*** Can't find server005n0.gbrac.ie: No answer

root@DNSServer:/etc/bind# nslookup server005n0
Server:         192.168.56.199
Address:        192.168.56.199#53

*** Can't find server005n0: No answer

```

Can someone take a look at my config files and explain what I am doing wrong?
I've set up bind before but with a domain IE .gbrac.ie

```
root@DNSServer:/etc/bind# cat server005.db
;
; BIND data file for local loopback interface
;
$TTL    86400
@       IN      SOA     server005.gbrac.ie root.server005.gbrac.ie (
                             17         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                          86400 )       ; Negative Cache TTL
;
@       IN      NS      server005.gbrac.ie
server005.gbrac.ie IN A 192.168.57.11
server005.gbrac.ie IN A 192.168.57.12
server005.gbrac.ie IN A 192.168.57.13




root@DNSServer:/etc/bind# cat server005n0.db
;
; BIND data file for local loopback interface
;
$TTL    86400
@       IN      SOA     server005n0-vip.gbrac.ie root.server005n0-vip.gbrac.ie (
                             18         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                          86400 )       ; Negative Cache TTL
;
@       IN      NS      server005n0-vip.gbrac.ie
server005n0-vip.gbrac.ie IN A 192.168.57.104
server005n0.gbrac.ie IN A 192.168.56.106




root@DNSServer:/etc/bind# cat server005n1.db
;
; BIND data file for local loopback interface
;
$TTL    86400
@       IN      SOA     server005n1-vip.gbrac.ie root.server005n1-vip.gbrac.ie (
                             18         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                          86400 )       ; Negative Cache TTL
;
@       IN      NS      server005n1-vip.gbrac.ie
server005n1-vip.gbrac.ie IN A 192.168.57.105
server005n1.gbrac.ie IN A 192.168.56.107




root@DNSServer:/etc/bind# cat named.conf.local
//
// Do any local configuration here
//

zone "58.168.192.in-addr.arpa" { type master; file "/etc/bind/58.168.192.in-addr.arpa"; };
zone "56.168.192.in-addr.arpa" { type master; file "/etc/bind/56.168.192.in-addr.arpa"; };
zone "server004" { type master; file "/etc/bind/server004.db"; };
zone "server004n0-vip" { type master; file "/etc/bind/server004n0.db"; };
zone "server004n1-vip" { type master; file "/etc/bind/server004n1.db"; };
zone "server004n0" { type master; file "/etc/bind/server004n0.db"; };
zone "server004n1" { type master; file "/etc/bind/server004n1.db"; };

zone "57.168.192.in-addr.arpa" { type master; file "/etc/bind/57.168.192.in-addr.arpa"; };
zone "server005" { type master; file "/etc/bind/server005.db"; };
zone "server005n0-vip" { type master; file "/etc/bind/server005n0.db"; };
zone "server005n1-vip" { type master; file "/etc/bind/server005n1.db"; };
zone "server005n0" { type master; file "/etc/bind/server005n0.db"; };
zone "server005n1" { type master; file "/etc/bind/server005n1.db"; };

zone "server005.gbrac.ie" { type master; file "/etc/bind/server005.db"; };
zone "server005n0-vip.gbrac.ie" { type master; file "/etc/bind/server005n0.db"; };
zone "server005n1-vip.gbrac.ie" { type master; file "/etc/bind/server005n1.db"; };
zone "server005n0.gbrac.ie" { type master; file "/etc/bind/server005n0.db"; };
zone "server005n1.gbrac.ie" { type master; file "/etc/bind/server005n1.db"; };

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";





root@DNSServer:/etc/bind# cat db.local
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     localhost. root.localhost. (
                              6         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      localhost.
@       IN      A       127.0.0.1
@       IN      A       192.168.56.199
@       IN      A       192.168.57.199
@       IN      AAAA    ::1

```

---

### Post by Doug S on 2013-02-07
What you are doing does not make sense to me. I think you should have one file for all forward lookups for your domain and one file for all reverse lookups.
I also don't understand why you say reverse lookups are working. For "nslookup 192.168.56.106" don't you want it to reply "server005n0.gbrac.ie" or "server005n0-vip.gbrac.ie" not what you have now "server005n0.gbrac.ie.56.168.192.in-addr.arpa."
Have a look at the Ubuntu server guide [chapter on bind]("https://help.ubuntu.com/12.04/serverguide/dns.html")

---

