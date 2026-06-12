---
title: "Ubuntu bind9 dns problem"
date: 2012-10-19
forum: Networking &amp; Wireless
---

### Post by Shinonuma on 2012-10-19
Hi, I'm trying to setup a DNS on my linux ubuntu 11.10

So here are the things that i've done:

First I changed the /etc/network/interfaces file:
```

auto eth0
iface eth0 inet static
address 192.168.56.20
netmask 255.255.255.0
network	192.168.56.0
broadcast 192.168.56.255
gateway 192.168.56.1
auto lo
iface lo inet loopback
```

Then I changed the /etc/resolvconf/resolv.conf.d/base file with

```
nameserver 192.168.56.20
nameserver 192.168.56.10
```

I installed bind9 and edited the /etc/bind/named.conf.local file 

```
//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "lintest.be"{
        type master;
        file "/etc/bind/zones/lintest.be.db";
}

```
Then I changed /etc/bind/named.conf.options because I got a DNS server on Windows Server 2008 aswell (both Linux & Windows server are running in VirtualBox on a host-only network) 

```
options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

recursion yes;

        forwarders {
                192.168.56.10;
        };

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```

In the /etc/bind/zones/lintest.be.db file:


```
$TTL 3D
@ IN SOA ns.mydomain.be. admin.mydomain.be. (
   2007062001
   28800
   3600
   604800
   38400
);
lintest.be.  IN      NS         ns.lintest.be.
mail     IN    CNAME  www
www             IN      A          192.168.56.10

```
When I want to lookup the dns server with nslookup mail.lintest.be I get this:

```
;; Got SERVFAIL reply from 192.168.56.20, trying next server
;; Got SERVFAIL reply from 127.0.0.1, trying next server
```

Does somebody know the problem?

---

### Post by jdthood on 2013-01-06
> **Shinonuma said:**
> 

First I changed the /etc/network/interfaces file:
```

auto eth0
iface eth0 inet static
address 192.168.56.20
netmask 255.255.255.0
network	192.168.56.0
broadcast 192.168.56.255
gateway 192.168.56.1
```
[...]

Then I changed the /etc/resolvconf/resolv.conf.d/base file with

```
nameserver 192.168.56.20
nameserver 192.168.56.10
```


This already looks very wrong.

1. Normally you don't need to put anything in resolv.conf.d/base.

2. What you have put in resolv.conf.d/base is an address of the local host. This will cause the glibc resolver always to look first for a nameserver running locally. If that is really what you want then leave resolv.conf.d/base empty and put
```

    RESOLVCONF=yes

```
in /etc/default/bind9.

---

### Post by jdthood on 2013-01-06
BTW, anyone interested in having bind9's forwarders list get dynamically updated, please add your voice to the following (wishlist) bug report.

    [https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1091602](https://bugs.launchpad.net/ubuntu/+source/bind9/+bug/1091602)

---

