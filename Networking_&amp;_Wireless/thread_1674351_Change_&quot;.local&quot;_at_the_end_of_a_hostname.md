---
title: "Change &quot;.local&quot; at the end of a hostname"
date: 2011-01-23
forum: Networking &amp; Wireless
---

### Post by 1v82TIn1 on 2011-01-23
I am trying to change the ".local" suffix on my Server's Hostname but i can't find the file that contains it. 

My router has ".iad" at the end of it so i suppose it would be possible to change it to something like ".com".

/etc/hostname just says:

toshiba-pc


and /etc/hosts just says:


10.0.0.11       toshiba-pc       # Added by NetworkManager
127.0.0.1       localhost.localdomain   localhost
::1     toshiba-pc       localhost6.localdomain6 localhost6
127.0.1.1       toshiba-pc

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Could somebody help me.

Thanks

---

