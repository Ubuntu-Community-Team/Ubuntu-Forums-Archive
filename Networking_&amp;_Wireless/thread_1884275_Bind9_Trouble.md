---
title: "Bind9 Trouble"
date: 2011-11-21
forum: Networking &amp; Wireless
---

### Post by Notebooks on 2011-11-21
I've been attempting to set up my own DNS server for a few days now, no matter what I try it doesn't seem to want to work. Intodns says the server isn't responding, but I know the ports are open, named is running, and everything is okay with my registrar.  :confused:

Here are my configs, replaced my domain with example.net:

/etc/bind/named.conf:
> 
options {
    directory "/etc/bind/zones";
};
zone "example.net" IN {
    type master;
    file "example.net.zone";
};
/etc/bind/zones/example.net.zone: (not my IP)
> 
$ORIGIN example.net.
$TTL 60
example.net.    IN SOA    ns1.example.net. example.gmail.com. (
    1008    ; Serial Number
    1200    ; Refresh
    180    ; Retry
    1209600    ; Expiry
    120    ; Minimum Time
    )

example.net. NS ns1.example.net.
example.net. NS ns2.example.net.

example.net.            A 208.67.222.222
ns1.example.net.        CNAME    example.net.
ns2.example.net.        CNAME    example.net.
[www.example.net]("http://www.example.net").        CNAME    example.net.


Anyone know what I've been missing? I've read every howto I could find on google and none of it has helped.](*,)

---

