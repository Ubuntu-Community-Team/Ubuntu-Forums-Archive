---
title: "HOWTO: Linux multihomed dns client"
date: 2010-04-11
forum: Networking &amp; Wireless
---

### Post by colemar on 2010-04-11
The Linux resolver queries all nameservers in the order they are listed in /etc/resolver.conf.
If a nameserver times out, it advances on to the following nameserver.
**But**, if a nameserver returns "not found" (NXDOMAIN) it stops.

This behaviour is problematic when you need to resolve names from the local domain along with names from the Internet.
Suppose you have two network interfaces, one for the private local area network (network interface card) and one for the public Internet (for example a vpn to a provider like Relakks). If you put the public nameserver first in resolver.conf, then all names in the local domain will not be resolved. If you put the private nameserver first, public site names will not be resolved.
The standard solution would be that the private nameserver infrastructure be able to resolve public names (i.e. do a recursive query for domains outside the local zone); but sometimes you find yourself attached to a private network that does not allow Internet access (or allow it only through a http proxy), hence the local nameservers do not have any reason to provide resolution for external names.

Windows has a concept in which a nameserver pertains to a particular network interface, therefore you can associate your ISP's nameserver to the vpn and the local nameserver to the network card. When the resolver is asked for the address corresponding to some name, it starts by querying the nameserver(s) associated to the preferred adapter (which happens to be the first in the "binding order"), failing that (by timeout or not-found) it advances to query nameservers associated to other adapters. In the end, any name which is resolvable by at least one involved nameserver will be resolved.

Linux has no built in rules to manage such a scenario.
I did much googling but found no answer about this problem.

I had a feeling that BIND (the Berkeley Internet Name Domain software, which is the standard nameserver daemon for Linux) could provide a solution, and indeed I found that the following works.

All work must be done as root.

Install bind9 package:
debian like Linux: aptitude install bind9
redhat like Linux: yum -y install bind9

You now have a local caching only nameserver, that is it does recursive queries for anything but the local host name. As it stands, it cannot resolve private domain names because it asks Internet dns root servers.

Save a copy of /etc/bind/named.conf and replace the original with:
```
options {
    directory "/var/cache/bind";

    forward only;

    forwarders {
        w.x.y.z; // your private nameserver
        8.8.8.8; // google-public-dns-a.google.com
    };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};

```That is, you have to add directives **forward** and **forwarders**, providing ip addresses for public and private nameservers.

Restart bind daemon:
service bind9 restart

Save a copy of /etc/resolv.conf and replace the original with:
```
nameserver 127.0.0.1
```This configuration somehow behaves like the Windows resolver, in that it does not stop at the first nameserver returning not-found.

As in the Windows case tough, sometimes some time is wasted asking to the wrong nameserver.
We can do better.

Let consider this version of named.conf

```
options {
    directory "/var/cache/bind";

    forward only;

    forwarders {
        8.8.8.8; // google-public-dns-a.google.com
    };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};

zone "your.domain" {
        type forward;
        forwarders {
                w.x.y.z; // your private nameserver
        };
};

```This configuration has the benefit that for names ending with your.domain the daemon does not bother to ask the public nameserver, and vice-versa.

---

