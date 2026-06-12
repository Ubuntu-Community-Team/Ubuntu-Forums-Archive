---
title: "/etc/event.d/hosts:1: Unknown stanza"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by thetick1 on 2009-08-22
During boot I get the following message:
/etc/event.d/hosts:1: Unknown stanza

The file is below.  XXXX is my machine name with a domain of home.  I commented out all the ip6 parms. Google searching has not helped me find out what is wrong.  Anyone have an idea?

127.0.0.1    localhost.home XXXX
127.0.1.1    XXXX

# The following lines are desirable for IPv6 capable hosts
#::1     localhost ip6-localhost ip6-loopback
#fe00::0 ip6-localnet
#ff00::0 ip6-mcastprefix
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters
#ff02::3 ip6-allhosts

---

### Post by Iowan on 2009-08-22
I've never looked in */etc/event.d* before... I suspect the same information is in */etc/hosts*. Try changing line #1 to read:```
127.0.0.1 localhost.home localhost
```

---

### Post by thetick1 on 2009-08-23
From what I googled the new upstart (replaces sysV init) uses the /etc/event.d structure so yes it is a copy of /etc/hosts.  Anyway I still get that message.  Networking works and I can still ping localhost and my alias so I guess it doesn't matter.

---

