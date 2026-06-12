---
title: "help with squid"
date: 2009-06-13
forum: Networking &amp; Wireless
---

### Post by W03L on 2009-06-13
hi.
there is ubuntu server eth0 (192.168.1.2) eth1 (192.168.50.1) wich taking internet from adsl modem (192.168.1.1 pppoe).

squid.conf
```

http_port 3128

acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/32

acl thisPC src 192.168.1.2/255.255.255.255
acl localnet src 192.168.50.0/24

cache_dir ufs /usr/local/squid/cache 5120 7 128
cache_swap_high 95
cache_swap_low 90
maximum_object_size 8192 KB
minimum_object_size 0 KB
quick_abort_pct 95

http_access allow manager localhost
http_access deny manager

http_access allow thisPC
http_access allow localnet
http_access deny all

access_log /usr/local/squid/log/access.log
cache_log /usr/local/squid/log/cache.log

```

I can't share internet with squid on client network 192.168.50.0/24
even after point gateway, dns - 192.168.50.1 and port - 3128 of proxy
what is wrong?

---

