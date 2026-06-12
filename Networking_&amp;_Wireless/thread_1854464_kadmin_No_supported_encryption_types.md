---
title: "kadmin: No supported encryption types"
date: 2011-10-04
forum: Networking &amp; Wireless
---

### Post by btnadiga on 2011-10-04
I'm trying to setup kerberos on Ubuntu 11.04

1) I changed krb5.conf. Do I need to restart anything? I do not see any krb5 related stuff in /etc/init.d

2) kadmin -p username produces the following error:
kadmin: No supported encryption types (config file error?) while initializing kadmin interface

Relevant lines from krb5.conf are:

[libdefaults]
    default_tgs_enctypes = des-cbc-crc
    default_tkt_enctypes = des-cbc-crc

Your help would be appreciated.
Thanks,
Balu

---

