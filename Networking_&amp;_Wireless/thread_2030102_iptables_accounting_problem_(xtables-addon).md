---
title: "iptables accounting problem (xtables-addon?)"
date: 2012-07-20
forum: Networking &amp; Wireless
---

### Post by jhtran on 2012-07-20
I'm trying to get iptables accounting working on Ubuntu 12.04 LTS
amd64 yet not having much luck.  Here is what I'm getting and I hope
someone can provide some insight to my problems:

root@ubuntu-mbp:~# dpkg -l|grep xtables
ii  xtables-addons-common                           1.40-1
                      Extensions targets and matches for iptables
[tools, libs]
ii  xtables-addons-dkms                             1.40-1
                      Extensions targets and matches for iptables
ii  xtables-addons-source                           1.40-1
                      Extensions targets and matches for iptables
[modules sources]
root@ubuntu-mbp:~# iptaccount -a

libxt_ACCOUNT_cl userspace accounting tool v1.3

get_table_names failed: Can't get table names from kernel. Out of
memory, MINBUFISZE too small?
root@ubuntu-mbp:~# iptaccount -u

libxt_ACCOUNT_cl userspace accounting tool v1.3

get_handle_usage failed: Can't get handle usage information from kernel

---

