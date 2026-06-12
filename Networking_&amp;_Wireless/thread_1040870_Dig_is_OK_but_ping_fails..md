---
title: "Dig is OK but ping fails."
date: 2009-01-16
forum: Networking &amp; Wireless
---

### Post by Feisei on 2009-01-16
I'm running bind9 on Ubuntu Server 8.10. I can use dig and nslookup without problems, but for some reason ping fails with the error "host unknown". Ping only fails when run on the actual nameserver machine. It runs fine when using another machine as can be seen from the output below.

Anyone got any idea what's going on?

result of "dig wchkris.wch.local":
```

; <<>> DiG 9.5.0-P2 <<>> wchkris.wch.local
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 2134
;; flags: qr aa rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 1, ADDITIONAL: 1

;; QUESTION SECTION:
;wchkris.wch.local.             IN      A

;; ANSWER SECTION:
wchkris.wch.local.      86400   IN      A       192.168.1.21

;; AUTHORITY SECTION:
wch.local.              86400   IN      NS      ns1.wch.local.

;; ADDITIONAL SECTION:
ns1.wch.local.          86400   IN      A       192.168.1.11

;; Query time: 0 msec
;; SERVER: 127.0.0.1#53(127.0.0.1)
;; WHEN: Fri Jan 16 14:08:57 2009
;; MSG SIZE  rcvd: 85

```

result of "ping wchkris.wch.local" when run on the actual server:
```
ping: unknown host wchkris.wch.local
```

result of "ping wchkris.wch.local" when run on another machine that uses the nameserver in question:
```
Pinging wchkris.wch.local [192.168.1.21] with 32 bytes of data:

Reply from 192.168.1.21: bytes=32 time<1ms TTL=128
Reply from 192.168.1.21: bytes=32 time<1ms TTL=128

Ping statistics for 192.168.1.21:
Packets: Sent = 2, Received = 2, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
Minimum = 0ms, Maximum = 0ms, Average = 0ms
```

/etc/bind/named.conf.local
```
zone "wch.local" {
        type master;
        file "/etc/bind/zones/wch.local.db";
        };

zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.1.168.192.in-addr.arpa";
};
```

/etc/bind/zones/wch.local.db
```
wch.local.      IN      SOA     ns1.wch.local. admin.wch.local. (
                        2009160103
                        4H
                        2H
                        4W
                        1D )

; ns1 is the nameserver for our network
; mail is the mailserver for our network
                IN      NS              ns1.wch.local.
                IN      MX     10       ns1.wch.local.

; setting some aliases
www             IN      CNAME           ns1.wch.local.
mail            IN      CNAME           ns1.wch.local.

; setting the hostnames
localhost       IN      A               127.0.0.1
router          IN      A               192.168.1.1
ns1             IN      A               192.168.1.11
wchkris         IN      A               192.168.1.21
sharp           IN      A               192.168.1.100
terastation     IN      A               192.168.1.200

; setting some extra information
ns1             IN      TXT             Dell Optiplex 755 - Chamonix Office - Service Tag: 2HYKDBX
router          IN      TXT             Corega Wireless G Router - Main Office
sharp           IN      TXT             Sharp MX-2700FG - Chamonix Office
terastation     IN      TXT             Buffalo TeraStation - Chamonix Office
```

rev.1.168.192.in-addr.arpa
```
1.168.192.in-addr.arpa. IN SOA ns1.wch.local. admin.wch.local. (
                        2009160102;
                        28800      ; refresh (8 hours)
                        14400      ; retry (4 hours)
                        3600000    ; expire (5 weeks 6 days 16 hours)
                        86400      ; minimum (1 day)
)

; define the authoritative name server
                        IN      NS      ns1.wch.local.
; our hosts
1                       IN      PTR     router
11                      IN      PTR     webserver
21                      IN      PTR     wchkris
100                     IN      PTR     sharp
200                     IN      PTR     terastation
```

/etc/nsswitch.conf
```
passwd:         compat
group:          compat
shadow:         compat

hosts:  files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

/etc/resolv.conf
```
nameserver 127.0.0.1
domain wch.local
```

---

