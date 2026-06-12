---
title: "Bind9 help for Newb"
date: 2009-01-20
forum: Networking &amp; Wireless
---

### Post by steelman on 2009-01-20
Trying to setup bind9 for home lab.  

Domain = steelman.local 


Bind9 fails on startup and indicates an error on line 22 of named.conf.  Beating my head against the wall trying to figure it out.  Used Ubuntu forum docs to create config.  Any help?


```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
        type hint;
        file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "steelman.local¨ {
        type master;
        **[COLOR="Red"]file "/etc/bind/db.steelman.local";[/COLOR]**
};

zone "0.0.127.in-addr.arpa" {
        type master;
        file "/etc/bind/db.127";
};

zone "1.168.192.in-addr.arpa" {
        type master;
        file "/etc/bind/db.192";
};

zone "255.in-addr.arpa" {
        type master;
        file "/etc/bind/db.255";
};

include "/etc/bind/named.conf.local";


```

---

### Post by MeneM on 2009-01-20
What does ```
ls -l /etc/bind/db.steelman.local
``` give us?

---

