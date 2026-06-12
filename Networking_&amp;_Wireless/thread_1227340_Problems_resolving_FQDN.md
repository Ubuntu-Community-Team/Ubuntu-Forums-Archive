---
title: "Problems resolving FQDN"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by Gutauckis on 2009-07-30
I am a bit confused as to why the following is not working as I would expect:

Using the Network tools I can be on the lookup tab and lookup "server1.example.local" and it resolves the full name properly. It does the same if I just look up "server1"

However when I try the Ping tab it only works if I use "server1". If I try to add the domain as in "server1.example.local" it does not work. From the CLI I get an unknown host error.

My /etc/hosts file:

```
127.0.0.1    localhost
127.0.1.1    ubuntu-one
127.0.0.1    ubuntu-one.example.local localhost ubuntu-one

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

My /etc/resolv.conf file:

```
nameserver 192.168.42.165
nameserver 192.168.42.229
domain example.local
```


This is on Ubuntu Desktop 9.04, just installed today with all updates. I spent about two hours playing with various settings but nothing has made a difference.

---

### Post by Gutauckis on 2009-07-31
Looks like I answered my question...

Changed resolution order from this:

```
files mdns4_minimal [NOTFOUND=return] dns mdns4
```

to this:

```
dns files mdns4_minimal [NOTFOUND=return] mdns4
```

and now its able to resolve the FQDN

---

