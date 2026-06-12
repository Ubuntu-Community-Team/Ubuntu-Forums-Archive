---
title: "Changes to nsswitch.conf don't allow changes to /etc/hosts file"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by codfather on 2009-12-21
Having read the documentation, many forum threads and many bugs, it would appear that if you want to have an IP address resolved from the /etc/hosts file you must edit /etc/nsswitch.conf.

The problem is this does't work on the following box:

Ubuntu 9.10
Kernel 2.6.31-16-generic-pae
All patches applied upto today

I have changed the /etc/nsswitch.conf file to look like this

# hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
hosts:          files dns
networks:       files

I have also stopped the avahi daemon to make sure it is not having an effect.

When I type in the DNS name of the host I have added into /etc/hosts, it is still getting resolved by DNS, which it shouldn't as I have specifically told it not too.

The hosts file contains this IPv4 address

1.2.3.4 nick.uk.company.com

I suspect that network manager or the resolver daemon are getting involved, but I can't for the life of me see how.

Any pointers gratefully received.

Nick

---

