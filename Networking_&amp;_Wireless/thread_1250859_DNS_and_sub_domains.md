---
title: "DNS and sub domains"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by abasel on 2009-08-27
I have had to set up the following in our DMZ

File: rosmini.school.nz.db

```

$TTL 3D
@ IN SOA ns.rosmini.school.nz. admin.rosmini.school.nz. (
   2007062001
   28800
   3600
   604800
   38400
);
rosmini.school.nz.  IN      NS         ns.rosmini.school.nz.
mail.student.rosmini.school.nz  IN      CNAME ghs.google.com.
start.student.rosmini.school.nz IN      CNAME ghs.google.com.
docs.student.rosmini.school.nz IN      CNAME ghs.google.com.
video.student.rosmini.school.nz IN      CNAME ghs.google.com.
myspace.student.rosmini.school.nz IN      CNAME ghs.google.com.
calendar.student.rosmini.school.nz IN      CNAME ghs.google.com.
www            IN      A          66.7.196.186
elearning       IN      A       172.16.0.2
sso             IN      A       172.16.0.5
gw             IN      A          172.16.0.254
                       TXT        "Network Gateway"
```

It all works well except the CNAME entries, which means that I can't get *.student.rosmini.school.nz to work in the DMZ.

The named.conf.local files looks as follows

```
# Our domain zone
zone "rosmini.school.nz" {
   type master;
   file "/etc/bind/zones/rosmini.school.nz.db";
};

# For reverse DNS
zone "0.16.172.in-addr.arpa" {
   type master;
   file "/etc/bind/zones/rev.0.16.172.in-addr.arpa";
};

```

What am I doing wrong?

---

