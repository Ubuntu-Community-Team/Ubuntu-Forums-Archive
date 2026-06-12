---
title: "BIND: can't get reverse lookup working"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by samsam009 on 2009-04-22
Hi, I have been working whole night last night to try to set up a PTR record in zone file, but the test is failed. I still can't nslookup ipaddress.

BIND version:
OS: FreeBSD 6.2

Test result from Vista:
C:\>nslookup 125.255.112.202
Server: UnKnown
Address: 192.168.1.254:53

*** UnKnown can't find 125.255.112.202: Non-existent domain

C:\>

C:\>nslookup ip6.com.au
Server: UnKnown
Address: 192.168.1.254:53

Non-authoritative answer:
Name: ip6.com.au
Address: 125.255.112.202

C:\>

zone file:
$TTL 200

@       IN      SOA     ns1.ip6.com.au. root.ip6.com.au.  (
                                2009042212
                                10800   ; Refresh
                                3600    ; Retry
                                604800  ; Expire
                                86400 ) ; Minimum
@       IN      NS      ns1.

202             IN      PTR     ip6.com.au.
202             IN      PTR     ns1.ip6.com.au.
202             IN      PTR     secure.ip6.com.au.
202             IN      PTR     [www.ip6.com.au](www.ip6.com.au).

Your help is very much appreciated.

Thanks

---

### Post by bapoumba on 2009-04-23
Moved to Networking.

---

