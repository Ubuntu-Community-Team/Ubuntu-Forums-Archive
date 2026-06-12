---
title: "Mpd"
date: 2009-08-02
forum: Multimedia Software
---

### Post by mpie on 2009-08-02
The answer for the MPD local host issue is nothing to do with MPD.

check your /etc/hosts file 

```
localhost 127.0.0.1
cpu-name 127.0.1.1
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


```

where cpu-name is what you chose at install
just match them up in you favorite editor, now looks like this

```
127.0.0.1	localhost
127.0.0.1	Corvidae-64
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

