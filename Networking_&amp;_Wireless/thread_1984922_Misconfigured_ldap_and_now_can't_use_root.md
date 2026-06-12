---
title: "Misconfigured ldap and now can't use root"
date: 2012-05-22
forum: Networking &amp; Wireless
---

### Post by again617 on 2012-05-22
I am running Ubuntu 12.04 and I tried to setup ldap client to run on it but I my ldap server is incorrect so login fails. However, when I attempt to use sudo to fix the ldap.conf file I get this error: 

```
sudo: setresuid(ROOT_UID, ROOT_UID, ROOT_UID): Operation not permitted
sudo: unable to open /var/lib/sudo/david/0: Operation not permitted
sudo: unable to set gid to run as gid 1001: Operation not permitted
sudo: unable to execute /usr/bin/vim: Operation not permitted
```

How do I fix my computer if I can not use root?

---

### Post by again617 on 2012-05-24
Well this issue is solved. I booted a live disc and restored my previous pam.d directory. I will hopefully be able to get ldap working in the future some time but at least I can use sudo again.

---

